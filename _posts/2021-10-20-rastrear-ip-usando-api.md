---
title: "Rastrear IP usando API"
excerpt: "Projeto para exibir a cidade e outra informações referente a um IP usando API ipgeolocation"
categories:
  - Projetos Web
tags:
  - Rastrear IP
  - IP
  - HTML
  - CSS
  - JS
  - API
  - ipgeolocation.io

toc: true
---

Este projeto exibe a localização estimada baseada no IP.  
A API por [ipgeolocation](https://ipgeolocation.io/).

Após inserir um endereço IPv4, a página deve retornar o local estimado deste IP, graças a API.

## Imagens 📷
![IPlocation1](https://user-images.githubusercontent.com/52220244/138132208-3f51a797-a760-43d5-9ede-582eb7735402.JPG)

![IPlocation2](https://user-images.githubusercontent.com/52220244/138132210-0e1f10d2-7d91-4fe4-a784-399427fc8c3a.JPG)

## Passos 📔

Crie uma pasta para armazenar todos os arquivos.

### index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Rastrear IP</title>
    <link rel="stylesheet" href="style.css">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://unpkg.com/boxicons@2.0.9/css/boxicons.min.css">
</head>
    <body>
        <div class="wrapper">
            <header><i class="bx bx-left-arrow-alt"></i>Rastrear IP</header>
            <section class="input-part">
                <p class="info-txt"></p>
                <input type="text" placeholder="Digite um IP" spellcheck="false" required>
                <div class="separator"></div>
                <button>Obter o IP do dispositivo</button>
            </section>
            <section class="ip-part">
                <img src="_" alt="Bandeira do país">
                <div class="location">
                    <div class="min-detail">
                        <i class='bx bxs-city'></i>
                        <span class="city">_, _</span>
                    </div>
                    <div class="other-locations">
                        <span class="continent">_, _</span>
                        <span class="country">_, _</span>
                        <span class="region">_, _</span>
                    </div>
                </div>
                <div class="map">
                    <i class='bx bx-map-alt'></i>
                    <span><a href="_" target="_blank"></a></span>
                </div>
                <div class="ip-address">
                    <i class='bx bxs-devices'></i>
                    <span>_</span>
                </div>
                <div class="bottom-details">
                    <div class="column feels">
                        <i class="bx bx-map"></i>
                        <div class="details">
                            <div class="lat-long">
                                <span>_, _</span>
                            </div>
                            <p>Latitude e longitude</p>
                        </div>
                    </div>
                    <div class="column security">
                        <i class='bx bx-check-shield' ></i>
                        <div class="details">
                            <span>_</span>
                            <p>VPN</p>
                        </div>
                    </div>
                    <div class="column currency">
                        <i class='bx bx-coin' ></i>
                        <div class="details">
                            <span>_, _</span>
                            <p>Moeda</p>
                        </div>
                    </div>
                    <div class="column timezone">
                        <i class='bx bx-time' ></i>
                        <div class="details">
                            <span>_:_:_</span>
                            <p>Horário</p>
                        </div>
                    </div>
                </div>
            </section>
        </div>

        <script src="script.js"></script>

    </body>
</html>
```

### style.css
```
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap');

:root {
    --cor-do-site: #742e06;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}
body {
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    background: var(--cor-do-site);
}
.wrapper {
    width: 600px;
    border-radius: 7px;
    background: #fff;
}
.wrapper header {
    color: var(--cor-do-site);
    font-size: 21px;
    font-weight: 500;
    padding: 16px 15px;
    display: flex;
    align-items: center;
    border-bottom: 1px solid #bfbfbf;
}
header i {
    cursor: pointer;
    font-size: 30px;
    margin-right: 8px;
}
.wrapper.active header {
    font-size: 30px;
    margin-left: 5px;
}
.wrapper .input-part {
    margin: 20px 25px 30px;
}
.wrapper.active .input-part {
    display: none;
}
.input-part .info-txt {
    display: none;
    font-size: 17px;
    text-align: center;
    padding: 12px 10px;
    border-radius: 7px;
    margin-bottom: 15px;
}
.info-txt.error {
    display: block;
    color: #721c24;
    background: #f8d7da;
    border: 1px solid #f5c6cb;
}
.info-txt.pending {
    display: block;
    color: #0c5460;
    background: #d1ecf1;
    border: 1px solid #bee5eb;
}
.input-part :where(input, button) {
    width: 100%;
    height: 55px;
    border: none;
    outline: none;
    font-size: 18px;
    border-radius: 7px;
}
.input-part input {
    text-align: center;
    border: 1px solid #bfbfbf;
}
.input-part input:is(:focus, :valid) {
    border: 2px solid var(--cor-do-site);
}
.input-part .separator {
    height: 1px;
    width: 100%;
    margin: 25px 0;
    background: #ccc;
    display: flex;
    align-items: center;
    justify-content: center;
}
.separator::before {
    content: "ou";
    color: #ccc;
    font-size: 19px;
    padding: 0 15px;
    background: #fff;
}
.input-part button {
    color: #fff;
    cursor: pointer;
    background: var(--cor-do-site);
}

.wrapper .ip-part {
    margin: 30px 0 0;
    display: none;
    align-items: center;
    justify-content: center;
    flex-direction: column;
}
.wrapper.active .ip-part {
    display: flex;
}
.ip-part img {
    max-width: 300px;
}
.ip-part .location {
    justify-content: center;
    font-size: 45px;
    font-weight: 500;
}
.ip-part .location .min-detail {
    display: flex;
    align-items: center;
}
.min-detail i {
    font-size: 45px;
    margin-right: 5px;
}
.ip-part .location .other-locations {
    display: flex;
    flex-direction: column;
    font-size: 28px;
    margin: 10px 5px 0 0;
}
.ip-part .location .city {
    font-weight: 600;
}
.map {
    display: flex;
    align-items: center;
    margin: 10px 5px 0 0;
}
.map i {
    font-size: 22px;
    margin-right: 5px;
}
.map span {
    font-size: 22px;
    font-weight: 600;
}
.map span a {
    text-decoration: underline;
}
.ip-part .ip-address {
    display: flex;
    align-items: center;
    font-size: 21px;
    margin: 10px 5px 30px 0;
}
.ip-address i {
    font-size: 22px;
    margin-right: 5px;
}
#mapid {
    height: 300px;
}
.ip-part .bottom-details {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    border-top: 1px solid #bfbfbf;
    justify-content: space-between;
}
.bottom-details .column {
    width: 100%;
    display: flex;
    flex: 1 0 50%; /* quebrar flex após certo tamanho */
    padding: 15px 0;
    align-items: center;
    justify-content: center;
}
.column i {
    color: var(--cor-do-site);
    font-size: 40px;
}
.column.security {
    border-left: 1px solid #bfbfbf;
}
.column.currency {
    border-left: 1px solid #bfbfbf;
    border-top: 1px solid #bfbfbf;
}
.column.timezone {
    border-left: 1px solid #bfbfbf;
    border-top: 1px solid #bfbfbf;
}
.details, .security span {
    font-size: 18px;
    font-weight: 500;
    margin-top: -3px;
}
.details .temp .deg {
    margin: 0;
    font-size: 17px;
    padding: 0 2px 0 1px;
}
.details p {
    font-size: 14px;
    margin-top: -6px;
}
```

### script.js
```
const wrapper = document.querySelector(".wrapper"),
inputPart = wrapper.querySelector(".input-part"),
infoTxt = inputPart.querySelector(".info-txt"),
inputField = inputPart.querySelector("input"),
localIpBtn = inputPart.querySelector("button"),
wIcon = wrapper.querySelector(".ip-part img"),
map = wrapper.querySelector(".map span a"),
arrowBack = wrapper.querySelector("header i");

const apiKey = 'API_KEY_CODE';
let api;

inputField.addEventListener("keyup", e => {
    // se pressionar o botão Enter e o valor não for nulo
    if (e.key == "Enter" && inputField.value != "") {
        requestApi(inputField.value);
    }
});

localIpBtn.addEventListener("click", () => {
    api = `https://ipgeolocation.abstractapi.com/v1/?api_key=${apiKey}&ip_address=`;
    fetchData();
});

function requestApi(ip) {
    api = `https://ipgeolocation.abstractapi.com/v1/?api_key=${apiKey}&ip_address=${ip}`;
    fetchData();
}

function fetchData() {
    infoTxt.innerText = "Obtendo detalhes do IP...";
    infoTxt.classList.add("pending");
    // coleta os dados da API e manda à função weatherDetails
    fetch(api).then(
        response => response.json().then(
            result => ipDetails(result)
        )
    );
}

function ipDetails(info) {
    infoTxt.classList.replace("pending", "error");
    if(info.cod == "404") {
        infoTxt.innerText = `${inputField.value} ocorreu um erro.`;
    } else {
        // coletando as informações do Json
        const {flag} = info;
        const {city, continent, continent_code, country, country_code, region, region_iso_code, ip_address, latitude, longitude, security, currency, timezone} = info;

        // passando as informações para um elemento HTML
        wIcon.src = flag.png;
        wrapper.querySelector(".city").innerText = `${city}, ${region_iso_code}`;
        wrapper.querySelector(".continent").innerText = `${continent}, ${continent_code}`;
        wrapper.querySelector(".country").innerText = `${country}, ${country_code}`;
        wrapper.querySelector(".region").innerText = `${region}, ${region_iso_code}`;
        map.href = `https://www.google.com/maps/search/${latitude},${longitude}/@2,12.9978113,17z?hl=pt-br`;
        wrapper.querySelector(".map span a").innerText = "Map Locaton";
        wrapper.querySelector(".ip-address span").innerText = ip_address;
        wrapper.querySelector(".lat-long span").innerText = `${latitude}, ${longitude}`;
        wrapper.querySelector(".security span").innerText = security.is_vpn;
        wrapper.querySelector(".currency span").innerText = `${currency.currency_code}, ${currency.currency_name}`;
        wrapper.querySelector(".timezone span").innerText = timezone.current_time;

        infoTxt.classList.remove("pending", "error");
        wrapper.classList.add("active");
    }
}

arrowBack.addEventListener("click", () => {
    wrapper.classList.remove("active");
});
```

> Lembre-se de criar uma conta no site, obter o seu código e substituir em API_KEY_CODE no arquivo script.js.

Agora é só abrir o index.html no navegador.

## Ferramentas usadas 🛠
- HTML and CSS
- JavaScript
- API