<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Rodi Mix Radio</title>
<style>
  body {
    font-family: Arial, sans-serif;
    background: #f0e6d2;
    color: #333;
    margin: 0;
    padding: 0;
    text-align: center;
  }
  header {
    background: #8B4513;
    color: white;
    padding: 20px;
  }
  header h1 {
    margin: 0;
  }
  .language-bar {
    margin-top: 10px;
  }
  .language-bar button {
    margin: 0 5px;
    padding: 10px 15px;
    border: none;
    background: #D2B48C;
    color: white;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
  }
  .language-bar button:hover {
    background: #c48b5c;
  }
  #player-box {
    margin: 20px auto;
    width: 90%;
  }
  iframe {
    width: 100%;
    height: 166px;
    border: none;
    border-radius: 10px;
  }
</style>
</head>
<body>

<header>
  <h1>🎧 Rodi Mix Radio</h1>
  <div class="language-bar">
    <button onclick="load('ar')">العربية</button>
    <button onclick="load('ku')">كردي</button>
    <button onclick="load('en')">English</button>
    <button onclick="load('de')">Deutsch</button>
  </div>
</header>

<div id="player-box"></div>

<script>
const links = {
  ar: "https://w.soundcloud.com/player/?url=https%3A//on.soundcloud.com/8F4OjyT2rhUL06Friu&auto_play=false",
  ku: "https://w.soundcloud.com/player/?url=https%3A//on.soundcloud.com/TRu6ULP4OOhHfDiSuq&auto_play=false",
  en: "https://w.soundcloud.com/player/?url=https%3A//on.soundcloud.com/uasUDhCcNVwcpXOmxw&auto_play=false",
  de: "https://w.soundcloud.com/player/?url=https%3A//on.soundcloud.com/8S47Uqyf05V&auto_play=false"
};

function load(lang){
  document.getElementById('player-box').innerHTML =
    `<iframe scrolling="no" frameborder="no" allow="autoplay" src="${links[lang]}"></iframe>`;
}

// تحميل اللغة العربية تلقائيًا عند فتح الصفحة
load('ar');
</script>

</body>
</html>
