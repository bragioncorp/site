---
title: "Windows Internals I"
excerpt: "Explicação do núcleo do sistema operacional Windows com foco em hacking."
categories:
  - Hacking
tags:
  - Windows Internals
  - User Mode
  - Kernel Mode
  - Win32
  - Native API
  - SSN
  - SSDT
  - EDR
  - EDR Hooking
  - Hooke Native API
  - ntdll.dll
  - Syscalls
  - Direct Syscall
  - Indirect Syscall

toc: true
---

# Windows Internals
Windows Internals mostra o funcionamento interno do sistema operacional Windows e quais são as principais partes do seu núcleo. Com um foco amplo na área de hacking e red team, o conhecimento sobre este tópico pode ser usado para ocultar e executar código, evitar detecções e encadear outras técnicas ou explorações.  
Alguns componentes do backend do Windows englobados por este tópico são os processos, formatos de arquivo, COM (Componente Objeto Model), programação de tarefas, sistema de I/O, etc.

# Kernel Mode vs User Mode
O privilégio no sistema Windows é dividido em dois modos: kernel mode e user mode. São melhor representados na imagem abaixo.  

![img1](https://upload.wikimedia.org/wikipedia/commons/2/2f/Priv_rings.svg)

O user-mode: executa aplicativos dos usuário com acesso limitado aos recursos do sistema. Atua de Ring 1 até Ring 3.   

O kernel-mode: possui acesso direto ao hardware e aos recursos do sistema principal. Atua apenas em Ring 0 e não são operados diretamente pelos programas.  

# Transferência de Privilégio
Em algum momento o programa precisará interagir com o kernel-mode para garantir que o programa funcione corretamente através da alocação de memórias, gravação direta no disco e modificação de permissões da memória. Para fazer isso de maneira segura, o Windows segue 3 etapas para transferir as instruções para o modo kernel.  

As etaps são:  
Win32 API → Native API → Kernel.  

# Wind32 API
São construídas com DLLs (Dynamic Link Librarys — como kernel32.dll) e cada DLL inclui funções para fazer chamadas e invocar a Native API para transferir a execução para ao kernal mode. Geralmente este termo se refere tanato a arquitetura de 32-bits quanto a de 64-bits.  

# DLLs
São bibliotecas compartilhadas que contêm código e dados usados por vários aplicativos simultaneamente. Fornecem as funções da Win32 API, permitindo que os programas vinculem e usem dinamicamente essas bibliotecas.

# Native API
É responsável por fazer a transição do user-mode para kernel-mode através de chamadas da instrução System Call (syscall) que reside em cada função Native API encontrada em NTDLL.dll. 

# System Calls (syscalls)
A instrução syscall é feita por aplicações em user-mode para o kernel-mode. Essas chamadas permitem que os aplicativos executem operações privilegiadas, como: entrada e saída de arquivos, criação de processos e gerenciamento e alocação de memória.  
Precisa ser especificada com um número especial (armazenado no registro eax de 32 bits) que o kernel requer para executar a rotina correta.  
Esse número é chamado de System Service Number (SSN) ecom ele o modo kernel executa algumas operações matemáticas e sabe qual sub-rotina kernel ele precisa executar para atender o requisito de programa.

![img2](https://static.wixstatic.com/media/6a4a49_2e78f3784df446c8bf4619edce8585cb~mv2.png/v1/fill/w_660,h_482,al_c,lg_1,q_85,enc_auto/6a4a49_2e78f3784df446c8bf4619edce8585cb~mv2.png)

# System Service Dispatch Table
A SSDT é uma tabela especial que reside no kernel-mode e é responsável por corresponder o número de syscall recebido pela Native API à uma sub-rotina do kernel que foi necessária para atender a solicitação de aplicação. O SSDT corresponde o SSN para sua respectiva sub-rotina através das seguintes operações matemáticas:  
- KiServiceTableAddress = Endereço do início da tabela SSDT.
- rotinaOffset = SSN que foi passado da Native API.

# EDR Hooking
É um mecanismo de defesa também conhecido como API Hooking. Quando um processo é criado, uma das primeiras coisas que são carregadas e alocadas no espaço de endereço virtual do processo é o ntdll.dll, a DLL que inclui todas as funções da Native API.  

Durante a inicialização do processo em um ambiente que apresenta EDR (Endpoint Detection and Response), um código é injetado pelo próprio EDR com algumas funções dentro do ntdll que redirecionam o fluxo de execução à DLL do EDR, o que permitirá que ele intercepte cada solicitação de Native API, inspecione o conteúdo e o contexto para o fluxo de execução e, de acordo com algumas regras ou assinaturas, verifique se há algum problema.  

Em seguida, o EDR decidirá se o programa tenta executar algum tipo de ação maliciosa, como a injeção de processo e, neste caso, acaba bloqueando a caminho até o syscall.  

Fluxo de execução com o EDR Hooking:  
![img2](https://miro.medium.com/v2/resize:fit:1400/1*QzZr--xITwgW4CCLPWbkfw.png)

Outro exemplo com a mesma função:  

![img3](https://redops.at/assets/images/blog/user-mode-hooking.png)

Observando as imagens acima, pode-se observar como o fluxo de execução está sendo redirecionado ao tentar executar uma função Hooked Native API chamada “NtAllocateMemory()”, uma função Native API usada para alocar memória virtual adicional a um processo.  

A seguir, através de um Disasembler (WinDbg), observa-se o jmp para uma seção de código EDR.

![img4](https://www.riskinsight-wavestone.com/wp-content/uploads/2023/10/07.png)

Abaixo há uma comparação entre um ambiente com e sem EDR, respectivamente.  

![img5](https://redops.at/assets/images/blog/windgb_comparison.png)

# Direct Syscalls
Uma das maneiras de evitar o EDR Hooking é atráves do Direct Syscall. Em vez de obter o código necessário no contexto das Native APIs para a transição do user-mode para o kernel-mode através do ntdll.dll, há a criação manual da função Native API que o programa deve percorrer, executando manualmente a instrução syscall e a transferência do fluxo de execução para o kernel-mode sem chamar as funções Hooked Native APIs.

![img6](https://redops.at/assets/images/blog/direct_syscalls_principle_2023-05-24-115444_nanc.png)

O único problema disso é que os SSN (System Service Number) não são os mesmos entre as versões do Windows e isso pode fazer o Direct Syscall uma técnica mais difícil de implementar se não pudermos dizer qual SSN precisamos de fato.  

Essa é uma técnica inteligente, mas infelizmente está sendo detectada por AVs e EDRs. O motivo da detecção é porque ao chamar diretamente a instrução Syscall no programa principal, é sinalizada como um COI (Indicador de Compromisso) por fornecedores de AV.

# Indirect Syscalls
É semelhante às syscalls diretas, mas apresenta uma diferença. Em vez de chamar diretamente a instrução Syscall do nosso programa, resolvemos o endereço da instrução Syscall dentro do NTDLL.dll e fazemos o programa saltar para o endereço da instrução Syscall dentro do NTDLL.dll e executar Syscall a partir daí. Isto irá ignorar os alertas do COI (Indicador de Compromisso) pelos AVs ao executar.

![img7](https://redops.at/assets/images/blog/indirect_syscalls_principle_2023-05-24-115519_fkdn.png)

O EDR nunca pode fazer Hook na própria instrução syscall. Isso é importante porque o EDR nunca pode nos impedir de executar a syscall na memória em ntdll.dll usando Indirect Syscalls.  

![img8](https://redops.at/assets/images/blog/api.png)