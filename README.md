Rodi.Radio

<html lang="ar">
<head>
<meta charset="UTF-8" />
<title>Rodi Mix Radio</title>
<style>
body {font-family:sans-serif;background:#eee;text-align:center;margin:0;padding:20px;}
button{margin:5px;padding:10px;border:none;background:#8B4513;color:#fff;cursor:pointer;}
iframe{width:100%;height:300px;border:none;margin-top:10px;}
</style>
</head>
<body>

<h2>🎧 Rodi Mix Radio</h2>

<button onclick="load('ar')">العربية</button>
<button onclick="load('ku')">كردي</button>
<button onclick="load('en')">English</button>
<button onclick="load('de')">Deutsch</button>

<div id="player-box"></div>

<script>
const links = {
  ku: "https://w.soundcloud.com/player/?url=https%3A//on.soundcloud.com/DcPby1GcftgsiZvyni&auto_play=false",
  ar: "https://w.soundcloud.com/player/?url=https%3A//on.soundcloud.com/mwqzAZESKvSpm7wGkg&auto_play=false",
  en: "https://w.soundcloud.com/player/?url=https%3A//on.soundcloud.com/ltqOpdrtZcT65IMTCl&auto_play=false",
  de: "https://w.soundcloud.com/player/?url=https%3A//on.soundcloud.com/X6WY3Sb2najjmmfSlI&auto_play=false"
};

function load(lang){
  document.getElementById('player-box').innerHTML =
    `<iframe src="${links[lang]}" allow="autoplay"></iframe>`;
}
</script>

</body>
</html>
