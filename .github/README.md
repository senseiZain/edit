<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Gerador de Sensi Free Fire</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background: #0d0d0d;
        color: #fff;
        text-align: center;
        padding: 20px;
    }
    h1 {
        color: #ff004c;
        text-shadow: 0 0 10px #ff004c;
    }
    .container {
        background: #1a1a1a;
        padding: 15px;
        border-radius: 15px;
        max-width: 450px;
        margin: auto;
        box-shadow: 0 0 20px #ff004c;
    }
    input, select {
        width: 90%;
        padding: 10px;
        margin: 8px;
        border-radius: 10px;
        border: none;
        font-size: 16px;
    }
    button {
        width: 90%;
        padding: 12px;
        background: #ff004c;
        color: white;
        border: none;
        border-radius: 12px;
        font-size: 18px;
        cursor: pointer;
        margin-top: 10px;
    }
    button:hover {
        background: #ff3366;
    }
    .resultado {
        margin-top: 15px;
        background: #222;
        padding: 12px;
        border-radius: 10px;
    }
    #manualBtn {
        position: fixed;
        right: 15px;
        bottom: 15px;
        background: #ff004c;
        color: #fff;
        font-size: 22px;
        border-radius: 50%;
        width: 50px;
        height: 50px;
        border: none;
        cursor: pointer;
        box-shadow: 0 0 10px #ff004c;
    }
    #manualModal {
        display: none;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0,0,0,0.8);
        justify-content: center;
        align-items: center;
    }
    #manualContent {
        background: #1a1a1a;
        padding: 20px;
        border-radius: 10px;
        max-width: 300px;
        text-align: left;
    }
</style>
</head>
<body>
<h1>Gerador de Sensi Free Fire</h1>
<div class="container">
    <input type="text" id="pesquisaModelo" placeholder="Pesquisar modelo...">
    <select id="modelo" size="8">
        <option>Motorola DynaTAC 8000X</option>
        <option>Moto G22</option>
        <option>Motorola One</option>
        <option>Moto G100</option>
        <option>Moto E7</option>
        <option>iPhone 4</option>
        <option>iPhone 5</option>
        <option>iPhone 6</option>
        <option>iPhone 7</option>
        <option>iPhone 8</option>
        <option>iPhone X</option>
        <option>iPhone 11</option>
        <option>iPhone 12</option>
        <option>iPhone 13</option>
        <option>iPhone 14</option>
        <option>iPhone 15 Pro</option>
        <option>Samsung Galaxy S3</option>
        <option>Samsung Galaxy S5</option>
        <option>Samsung Galaxy S7</option>
        <option>Samsung Galaxy S9</option>
        <option>Samsung Galaxy S10</option>
        <option>Samsung Galaxy S20</option>
        <option>Samsung Galaxy S21</option>
        <option>Samsung Galaxy S22</option>
        <option>Samsung Galaxy S23</option>
        <option>Samsung Galaxy S24 Ultra</option>
        <option>Redmi Note 7</option>
        <option>Redmi Note 8</option>
        <option>Redmi Note 9</option>
        <option>Redmi Note 10</option>
        <option>Redmi Note 11</option>
        <option>Redmi Note 12 Pro</option>
        <option>Huawei P30</option>
        <option>Huawei P40</option>
        <option>Huawei Mate 40 Pro</option>
        <option>Outro</option>
    </select>

    <select id="estilo">
        <option>2 Dedos</option>
        <option>3 Dedos</option>
        <option>4 Dedos</option>
        <option>5 Dedos</option>
    </select>

    <select id="botao">
        <option>Pequeno</option>
        <option>Médio</option>
        <option>Grande</option>
    </select>

    <select id="dpiOption">
        <option>Sem DPI</option>
        <option>Com DPI</option>
    </select>

    <select id="tipo">
        <option>Free Fire Normal</option>
        <option>Free Fire MAX</option>
    </select>

    <input type="number" id="nivel" placeholder="Nível (0% a 200%)" min="0" max="200">

    <button onclick="gerarSensi()">GERAR SENSI</button>
    <div class="resultado" id="resultado"></div>
</div>

<button id="manualBtn">ℹ️</button>

<div id="manualModal">
    <div id="manualContent">
        <h2>Manual de Instruções</h2>
        <ol>
            <li>Pesquise e selecione seu celular</li>
            <li>Escolha estilo (2 a 5 dedos)</li>
            <li>Defina tamanho de botões</li>
            <li>Escolha com DPI ou não</li>
            <li>Selecione Free Fire Normal ou MAX</li>
            <li>Digite nível (0% a 200%)</li>
            <li>Clique em GERAR e copie as configs</li>
        </ol>
        <button onclick="fecharManual()">Fechar</button>
    </div>
</div>

<script>
document.getElementById("pesquisaModelo").addEventListener("input", function() {
    let filtro = this.value.toLowerCase();
    let options = document.querySelectorAll("#modelo option");
    options.forEach(opt => {
        if (opt.text.toLowerCase().includes(filtro)) {
            opt.style.display = "";
        } else {
            opt.style.display = "none";
        }
    });
});

document.getElementById("manualBtn").onclick = () => {
    document.getElementById("manualModal").style.display = "flex";
};
function fecharManual() {
    document.getElementById("manualModal").style.display = "none";
}

function gerarSensi() {
    let modelo = document.getElementById("modelo").value;
    let dpiOption = document.getElementById("dpiOption").value;
    let nivel = parseInt(document.getElementById("nivel").value) || 100;
    let base = nivel / 100;

    let dpi = 0;
    if (dpiOption === "Com DPI") {
        if (modelo.includes("Moto")) dpi = 450;
        else if (modelo.includes("Motorola One")) dpi = 411;
        else if (modelo.includes("iPhone")) dpi = 0;
        else if (modelo.includes("Samsung")) dpi = 600;
        else dpi = 500;
    }

    let geral = Math.min(100, Math.floor(80 * base));
    let mira = Math.min(100, Math.floor(75 * base));
    let redDot = Math.min(100, Math.floor(70 * base));
    let x2 = Math.min(100, Math.floor(65 * base));
    let x4 = Math.min(100, Math.floor(60 * base));
    let awm = Math.min(100, Math.floor(55 * base));

    document.getElementById("resultado").innerHTML = `
        <h3>Sua Sensi Perfeita</h3>
        <p>DPI: ${dpi > 0 ? dpi : "Não usar DPI"}</p>
        <p>Geral: ${geral}</p>
        <p>Mira: ${mira}</p>
        <p>Red Dot: ${redDot}</p>
        <p>2X: ${x2}</p>
        <p>4X: ${x4}</p>
        <p>AWM: ${awm}</p>
    `;
}
</script>
</body>
</html>