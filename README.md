# Rodi.Radio
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Rodi Mix Radio</title>
<style>
body { font-family: Arial, sans-serif; margin: 0; padding: 0; background: #f0e6d2; color: #333; }
header { background: #8B4513; color: white; padding: 20px; text-align: center; }
.language-bar button { margin: 0 5px; padding: 5px 10px; border: none; background: #D2B48C; color: white; border-radius: 5px; cursor: pointer; }
.song-section { padding: 20px; }
.song-list, .playlist { margin-top: 10px; }
.song-item, .playlist-item { background: white; padding: 10px; border-radius: 10px; margin-bottom: 10px; cursor: pointer; }
.song-item button { margin-top: 5px; }
footer { position: fixed; bottom: 0; width: 100%; background: #8B4513; color: white; padding: 10px; text-align: center; }
</style>
</head>
<body>
<header>
<h1>Rodi Mix Radio</h1>
<div class="language-bar">
<button onclick="switchLanguage('ku')">كردي</button>
<button onclick="switchLanguage('ar')">عربي</button>
<button onclick="switchLanguage('en')">English</button>
<button onclick="switchLanguage('de')">Deutsch</button>
</div>
</header>

<div class="song-section">
<h2 id="section-title">Songs</h2>
<div class="song-list" id="song-list"></div>

<h3>Add New Song</h3>
<input type="text" id="song-title" placeholder="Song Title">
<input type="text" id="song-artist" placeholder="Artist">
<input type="text" id="song-src" placeholder="MP3 URL">
<button onclick="addNewSong()">Add Song</button>

<div class="playlist" id="playlist">
<h3>Playlist</h3>
<div id="playlist-items"></div>
</div>
</div>

<footer>
<div class="player-controls">
<button onclick="prevSong()">⏮️ Previous</button>
<button onclick="playPause()">▶️ Play/Pause</button>
<button onclick="nextSong()">⏭️ Next</button>
</div>
</footer>

<script>
let songs = {
  ku: [
    { title: "Kurdish Playlist", artist: "Various", src: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" }
  ],
  ar: [
    { title: "Arabic Playlist", artist: "Various", src: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3" }
  ],
  en: [
    { title: "English Playlist", artist: "Various", src: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-3.mp3" }
  ],
  de: [
    { title: "German Playlist", artist: "Various", src: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-4.mp3" }
  ]
};

let currentLang = 'ku';
let playlist = [];
let audio = new Audio();
let currentIndex = 0;

function switchLanguage(lang) {
  currentLang = lang;
  loadSongs();
  updatePlaylist();
}

function loadSongs() {
  const songList = document.getElementById('song-list');
  const sectionTitle = document.getElementById('section-title');
  songList.innerHTML = '';
  const langTitles = { ku: 'Stran', ar: 'أغاني', en: 'Songs', de: 'Lieder' };
  sectionTitle.textContent = langTitles[currentLang];

  songs[currentLang].forEach((song, index) => {
    const div = document.createElement('div');
    div.className = 'song-item';
    div.innerHTML = `<strong>${song.title}</strong><br>${song.artist}<br><button onclick='playSong(${index})'>▶️ Play</button> <button onclick='addToPlaylist(${index})'>➕ Add to Playlist</button>`;
    songList.appendChild(div);
  });
}

function addNewSong() {
  const title = document.getElementById('song-title').value;
  const artist = document.getElementById('song-artist').value;
  const src = document.getElementById('song-src').value;
  if(title && artist && src) {
    const newSong = { title, artist, src };
    songs[currentLang].push(newSong);
    document.getElementById('song-title').value='';
    document.getElementById('song-artist').value='';
    document.getElementById('song-src').value='';
    loadSongs();
    alert('Song added!');
  } else {
    alert('Please fill all fields.');
  }
}

function playSong(index) {
  currentIndex = index;
  playCurrentSong();
}

function playCurrentSong() {
  audio.src = playlist.length>0 ? playlist[currentIndex].src : songs[currentLang][currentIndex].src;
  audio.play();
}

function playPause() { if(audio.paused) audio.play(); else audio.pause(); }
function nextSong() { currentIndex = (currentIndex + 1) % (playlist.length>0 ? playlist.length : songs[currentLang].length); playCurrentSong(); }
function prevSong() { currentIndex = (currentIndex - 1 + (playlist.length>0 ? playlist.length : songs[currentLang].length)) % (playlist.length>0 ? playlist.length : songs[currentLang].length); playCurrentSong(); }
function addToPlaylist(index) { const song = songs[currentLang][index]; playlist.push(song); updatePlaylist(); }
function updatePlaylist() { const div = document.getElementById('playlist-items'); div.innerHTML=''; playlist.forEach((song, idx)=>{ const item = document.createElement('div'); item.className='playlist-item'; item.textContent=`${song.title} - ${song.artist}`; item.onclick = ()=>{ currentIndex=idx; playCurrentSong(); }; div.appendChild(item); }); }

window.onload = ()=>{ loadSongs(); updatePlaylist(); };
</script>
</body>
</html>
