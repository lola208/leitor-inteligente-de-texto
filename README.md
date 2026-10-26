<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Leitor Inteligente de Texto</title>
 
<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family: Arial, sans-serif;
}
 
body{
background: #eef3f8;
display:flex;
justify-content:center;
align-items:center;
min-height:100vh;
}
 
.container{
background:white;
width:90%;
max-width:700px;
padding:30px;
border-radius:15px;
box-shadow:0 4px 15px rgba(0,0,0,0.15);
}
 
h1{
text-align:center;
color:#0066cc;
margin-bottom:20px;
}
 
textarea{
width:100%;
height:180px;
padding:15px;
border:1px solid #ccc;
border-radius:8px;
resize:none;
margin-bottom:20px;
font-size:16px;
}
 
.buttons{
display:flex;
gap:15px;
flex-wrap:wrap;
}
 
button{
flex:1;
padding:12px;
border:none;
border-radius:8px;
font-size:16px;
cursor:pointer;
color:white;
}
 
#ler{
background:#28a745;
}
 
#parar{
background:#dc3545;
}
 
.status{
margin-top:20px;
padding:15px;
background:#f4f4f4;
border-radius:8px;
text-align:center;
font-weight:bold;
}
</style>
</head>
<body>
 
<div class="container">
 
<h1>Leitor Inteligente de Texto</h1>
 
<textarea id="texto">
A segurança digital é essencial para proteger informações pessoais e evitar golpes na internet. Antes de clicar em links recebidos, verifique sempre a origem da mensagem.
</textarea>
 
<div class="buttons">
<button id="ler">🔊 Iniciar Leitura</button>
<button id="parar">⏹ Parar Leitura</button>
</div>
 
<div class="status" id="status">
Nenhuma leitura em execução.
</div>
 
</div>
 
<script>
 
let leituraAtual = null;
 
const texto = document.getElementById("texto");
const btnLer = document.getElementById("ler");
const btnParar = document.getElementById("parar");
const status = document.getElementById("status");
 
btnLer.addEventListener("click", () => {
 
speechSynthesis.cancel();
 
leituraAtual = new SpeechSynthesisUtterance(texto.value);
 
status.textContent = "Leitura em andamento...";
 
leituraAtual.onend = () => {
status.textContent = "Leitura concluída.";
};
 
speechSynthesis.speak(leituraAtual);
});
 
btnParar.addEventListener("click", () => {
speechSynthesis.cancel();
status.textContent = "Leitura interrompida.";
});
 
</script>
 
</body>
</html>
