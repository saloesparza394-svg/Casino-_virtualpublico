from pathlib import Path

html = """<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Casino Virtual 2.0</title>
<style>
body{font-family:Arial;margin:0;background:#111827;color:white}.app{max-width:500px;margin:auto;padding:18px}
.card{background:#1f2937;border-radius:18px;padding:18px;margin-bottom:14px}
h1{text-align:center}.saldo{text-align:center;font-size:25px;font-weight:bold}
.wheel{text-align:center;font-size:75px;margin:15px}.buttons{display:grid;grid-template-columns:1fr 1fr;gap:8px}
button,input{font-size:18px;padding:13px;border-radius:10px;border:0}button{background:#f2c14e;font-weight:bold}
input{width:90px}.resultado{text-align:center;font-size:20px;margin-top:12px;min-height:28px}
small{color:#bbb}
</style>
</head>
<body><div class="app">
<div class="card"><h1>🎰 Casino Virtual 2.0</h1><div class="saldo">🪙 <span id="saldo">1000</span> fichas</div></div>
<div class="card"><h2>🎡 Ruleta</h2><div class="wheel" id="rueda">🎡</div>
<div>Apuesta: <input id="apuesta" type="number" value="50" min="1"></div>
<div class="buttons">
<button onclick="jugar('rojo')">🔴 Rojo</button><button onclick="jugar('negro')">⚫ Negro</button>
<button onclick="jugar('par')">Par</button><button onclick="jugar('impar')">Impar</button>
</div><div class="resultado" id="resultado"></div></div>
<div class="card"><h3>🃏 Blackjack</h3><p>Próximamente</p><h3>🎲 Dados</h3><p>Próximamente</p><h3>🏆 Ranking</h3><p>Próximamente</p></div>
<small>Solo fichas virtuales sin valor monetario. Sin depósitos ni retiros de dinero real.</small>
</div>
<script>
let saldo=1000;
function jugar(tipo){
 let a=Math.floor(Number(document.getElementById('apuesta').value));
 let r=document.getElementById('resultado');
 if(a<1||a>saldo){r.textContent='Apuesta no válida.';return}
 let n=Math.floor(Math.random()*37), color=n===0?'verde':n%2?'rojo':'negro';
 let gana=tipo==='rojo'||tipo==='negro'?color===tipo:(tipo==='par'?n!==0&&n%2===0:n!==0&&n%2!==0);
 saldo+=gana?a:-a; document.getElementById('saldo').textContent=saldo;
 document.getElementById('rueda').textContent='🎡 '+n;
 r.textContent=gana?'¡Ganaste '+a+' fichas! 🎉':'Perdiste '+a+' fichas.';
}
</script></body></html>"""
p=Path("/mnt/data/Casino_Virtual_2_0.html")
p.write_text(html,encoding="utf-8")
print(f"[Descargar Casino Virtual 2.0](sandbox:{p})")
