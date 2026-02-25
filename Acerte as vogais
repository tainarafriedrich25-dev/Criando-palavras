<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Vogais no Céu</title>

<style>
body{
  margin:0;
  font-family: Arial, sans-serif;
  text-align:center;
  background: linear-gradient(to bottom, #87CEEB, #E0F6FF);
  overflow-x:hidden;
}

h1{
  margin-top:20px;
  color:#003049;
}

#palavra{
  font-size:42px;
  letter-spacing:15px;
  margin:40px;
}

.espaco{
  display:inline-block;
  width:55px;
  height:55px;
  border:3px dashed #003049;
  vertical-align:middle;
  background:white;
}

.nuvens{
  margin-top:40px;
}

.nuvem{
  display:inline-block;
  width:100px;
  height:60px;
  background:white;
  border-radius:50px;
  margin:15px;
  position:relative;
  cursor:grab;
  box-shadow:0 5px 10px rgba(0,0,0,0.2);
}

.nuvem:before,
.nuvem:after{
  content:"";
  position:absolute;
  background:white;
  width:60px;
  height:60px;
  border-radius:50%;
  top:-30px;
}

.nuvem:before{ left:10px; }
.nuvem:after{ right:10px; }

.letra{
  position:absolute;
  top:50%;
  left:50%;
  transform:translate(-50%, -50%);
  font-size:28px;
  font-weight:bold;
  color:#003049;
}

#resultado{
  font-size:22px;
  margin-top:20px;
  font-weight:bold;
}

#pontos{
  font-size:18px;
  margin-top:10px;
}
</style>
</head>

<body>

<h1>☁️ Complete com as Vogais ☁️</h1>

<div id="palavra"></div>

<div class="nuvens" id="vogaisContainer"></div>

<p id="resultado"></p>
<p id="pontos">Pontos: 0</p>

<script>

let palavras = [
  "CASA","BOLA","MESA","SAPO","LOBO",
  "GATO","PATO","DADO","FADA","VACA",
  "FITA","RATO","LATA","BICO","LIVRO"
];

let palavraAtual = "";
let vogaisCorretas = [];
let acertos = 0;
let pontos = 0;

function novaPalavra(){

  acertos = 0;
  document.getElementById("resultado").innerHTML = "";

  palavraAtual = palavras[Math.floor(Math.random()*palavras.length)];

  let exibicao = "";
  vogaisCorretas = [];

  for(let i=0;i<palavraAtual.length;i++){
    let letra = palavraAtual[i];

    if("AEIOU".includes(letra)){
      exibicao += `<div class="espaco" 
      ondrop="drop(event,'${letra}')" 
      ondragover="allowDrop(event)"></div>`;
      vogaisCorretas.push(letra);
    }else{
      exibicao += letra + " ";
    }
  }

  document.getElementById("palavra").innerHTML = exibicao;
}

function criarVogais(){
  let container = document.getElementById("vogaisContainer");
  container.innerHTML = "";

  let vogais = ["A","E","I","O","U"];

  vogais.forEach(v => {
    container.innerHTML += `
      <div class="nuvem" draggable="true" 
      ondragstart="drag(event)" id="${v}">
        <div class="letra">${v}</div>
      </div>`;
  });
}

function allowDrop(ev){
  ev.preventDefault();
}

function drag(ev){
  ev.dataTransfer.setData("text", ev.target.id);
}

function drop(ev, correta){
  ev.preventDefault();
  let data = ev.dataTransfer.getData("text");

  if(data === correta){
    ev.target.innerHTML = data;
    ev.target.style.border = "3px solid green";
    acertos++;

    if(acertos === vogaisCorretas.length){
      pontos += 10;
      document.getElementById("resultado").innerHTML =
      "✅ Muito bem! Palavra correta: " + palavraAtual;
      document.getElementById("pontos").innerHTML =
      "Pontos: " + pontos;

      setTimeout(novaPalavra,1500);
    }

  }else{
    document.getElementById("resultado").innerHTML =
    "❌ Vogal incorreta. Tente novamente!";
  }
}

criarVogais();
novaPalavra();

</script>

</body>
</html>
