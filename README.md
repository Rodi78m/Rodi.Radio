Rodi.Mix
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>Rodi Mix Radio</title>
  <style>
    * {
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
    }
    
    body {
      font-family: 'Segoe UI', 'Roboto', 'Noto Sans Arabic', sans-serif;
      background: #f7f3e9;
      text-align: center;
      margin: 0;
      padding: 15px;
      color: #333;
      min-height: 100vh;
      touch-action: manipulation;
    }
    
    h2 {
      color: #8B4513;
      margin-top: 0;
      font-size: 1.5rem;
      padding: 10px 0;
    }
    
    .instructions {
      background: #fff8e6;
      border: 1px solid #ffd54f;
      border-radius: 10px;
      padding: 12px;
      margin: 10px 0;
      text-align: center;
      font-size: 0.95rem;
      color: #5d4037;
    }
    
    .language-bar {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
      margin: 15px 0;
    }
    
    button {
      flex: 1;
      min-width: 120px;
      padding: 14px 10px;
      border: none;
      background: #8B4513;
      color: #fff;
      cursor: pointer;
      border-radius: 12px;
      font-size: 1.1rem;
      transition: all 0.3s ease;
      box-shadow: 0 3px 6px rgba(0,0,0,0.1);
      touch-action: manipulation;
      user-select: none;
      overflow: hidden;
      position: relative;
    }
    
    button:active {
      transform: scale(0.97);
      box-shadow: 0 2px 4px rgba(0,0,0,0.15);
    }
    
    button::after {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      width: 5px;
      height: 5px;
      background: rgba(255,255,255,0.5);
      opacity: 0;
      border-radius: 100%;
      transform: scale(1, 1) translate(-50%);
      transform-origin: 50% 50%;
    }
    
    button:active::after {
      animation: ripple 1s ease-out;
      opacity: 0.3;
    }
    
    @keyframes ripple {
      0% {
        transform: scale(0, 0);
        opacity: 0.5;
      }
      20% {
        transform: scale(20, 20);
        opacity: 0.3;
      }
      100% {
        transform: scale(200, 200);
        opacity: 0;
      }
    }
    
    .player-container {
      width: 100%;
      max-width: 700px;
      margin: 0 auto 20px;
      border-radius: 16px;
      overflow: hidden;
      box-shadow: 0 6px 16px rgba(0,0,0,0.15);
      background: white;
    }
    
    iframe {
      width: 100%;
      height: 166px;
      border: none;
      border-radius: 16px;
      background: #f5f5f5;
    }
    
    .track-list {
      width: 100%;
      max-width: 700px;
      margin: 0 auto 25px;
      background: white;
      border-radius: 16px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
      padding: 15px;
      text-align: right;
      overflow: hidden;
    }
    
    .track-list h3 {
      margin-top: 0;
      color: #8B4513;
      font-size: 1.2rem;
      padding-bottom: 8px;
      border-bottom: 1px solid #eee;
    }
    
    .track-item {
      display: flex;
      flex-direction: column;
      padding: 12px 10px;
      border-bottom: 1px solid #f5f5f5;
      font-size: 0.95rem;
      transition: background 0.2s;
    }
    
    .track-item:last-child {
      border-bottom: none;
    }
    
    .track-item:active {
      background: #f9f7f3;
    }
    
    .track-title {
      font-weight: bold;
      color: #5a3921;
      margin-bottom: 4px;
      font-size: 1.05rem;
    }
    
    .track-artist {
      color: #333;
      font-size: 0.95rem;
      margin-bottom: 4px;
    }
    
    .track-stats {
      color: #8B4513;
      font-size: 0.85rem;
      text-align: left;
    }
    
    .status-indicator {
      display: inline-block;
      width: 10px;
      height: 10px;
      background: #4CAF50;
      border-radius: 50%;
      margin-left: 6px;
      vertical-align: middle;
    }
    
    .loading {
      height: 3px;
      background: #8B4513;
      width: 0%;
      transition: width 0.3s;
      position: relative;
      top: -1px;
    }
    
    .footer {
      margin-top: 20px;
      padding: 15px 0;
      color: #777;
      font-size: 0.85rem;
      border-top: 1px solid #eee;
    }
    
    /* تصميم مخصص لأجهزة أندرويد */
    @media (pointer: coarse) {
      button {
        padding: 16px 10px;
        min-height: 50px;
        font-size: 1.15rem;
      }
      
      .track-item {
        padding: 14px 12px;
      }
      
      iframe {
        height: 180px;
      }
    }
    
    /* تصميم للشاشات الصغيرة جداً */
    @media (max-width: 360px) {
      button {
        padding: 12px 8px;
        min-width: 100px;
        font-size: 1rem;
      }
      
      h2 {
        font-size: 1.3rem;
      }
      
      .track-title {
        font-size: 0.95rem;
      }
      
      .track-artist, .track-stats {
        font-size: 0.85rem;
      }
    }
  </style>
</head>
<body>

  <h2>🎧 Rodi Mix Radio</h2>
  
  <div class="instructions">
    <span class="status-indicator"></span> اضغط على زر اللغة لبدء التشغيل
  </div>

  <div class="language-bar">
    <button onclick="load('ku')">كردي</button>
    <button onclick="load('ar')">العربية</button>
    <button onclick="load('en')">English</button>
    <button onclick="load('de')">Deutsch</button>
  </div>

  <div class="player-container">
    <div class="loading" id="loading-bar"></div>
    <div id="player-box"></div>
  </div>
  
  <div id="track-list"></div>
  
  <div class="footer">
    يعمل على جميع الأجهزة بما في ذلك أندرويد | نسخة 2.0
  </div>

  <script>
    // الروابط مع التشغيل التلقائي
    const players = {
      ku: "https://w.soundcloud.com/player/?url=https%3A//soundcloud.com/yusuf-i-k-685870955/sets/kurdish-music&color=%23ff5500&auto_play=true&hide_related=true&show_comments=false&show_user=true&show_reposts=false&show_teaser=false",
      ar: "https://w.soundcloud.com/player/?url=https%3A//soundcloud.com/bader-alzman/sets/2025a1&color=%23ff5500&auto_play=true&hide_related=true&show_comments=false&show_user=true&show_reposts=false&show_teaser=false",
      en: "https://w.soundcloud.com/player/?url=https%3A//soundcloud.com/turbulentz/sets/clean-hits-2025-best-pop-clean&color=%23ff5500&auto_play=true&hide_related=true&show_comments=false&show_user=true&show_reposts=false&show_teaser=false",
      de: "https://w.soundcloud.com/player/?url=https%3A//soundcloud.com/user-218498324/sets/deutsch-rap-remix&color=%23ff5500&auto_play=true&hide_related=true&show_comments=false&show_user=true&show_reposts=false&show_teaser=false"
    };

    // قوائم الأغاني من المحتوى الفعلي
    const tracks = {
      // الأغاني الكردية - من المحتوى الجديد
      ku: [
        { title: "Ez Kurdistan Im", artist: "Serhado", plays: "" },
        { title: "Zap Zap Zape", artist: "sanliurfaHDP", plays: "" },
        { title: "Awaze Ciya Kato", artist: "Kadar Baze Kurdi", plays: "" },
        { title: "Awazê Çiya | Navê Wê", artist: "ewrêdeng", plays: "" },
        { title: "Awaze çiya - biji biji ypg", artist: "kurdishmusics", plays: "" }
      ],
      // الأغاني العربية - قائمة محدثة
      ar: [
        { title: "أغنية 1", artist: "فنان 1", plays: "" },
        { title: "أغنية 2", artist: "فنان 2", plays: "" },
        { title: "أغنية 3", artist: "فنان 3", plays: "" },
        { title: "أغنية 4", artist: "فنان 4", plays: "" },
        { title: "أغنية 5", artist: "فنان 5", plays: "" }
      ],
      // الأغاني الإنجليزية - من المحتوى الجديد
      en: [
        { title: "Ssio ehrenloser remix", artist: "Nikurazu", plays: "" },
        { title: "Paris Freestyle x Gangstas Paradise", artist: "r58", plays: "" },
        { title: "Airwaves Remix", artist: "roland", plays: "" },
        { title: "SSIO - HASH HASH x Barbra Streisand", artist: "FW", plays: "" },
        { title: "SSIO vs. Usher - Yeah Nuttööö", artist: "Daniel Hein Mashups", plays: "" }
      ],
      // الأغاني الألمانية - من المحتوى الجديد
      de: [
        { title: "Ssio ehrenloser remix", artist: "Nikurazu", plays: "" },
        { title: "Paris Freestyle x Gangstas Paradise", artist: "r58", plays: "" },
        { title: "Airwaves Remix", artist: "roland", plays: "" },
        { title: "SSIO - HASH HASH x Barbra Streisand", artist: "FW", plays: "" },
        { title: "SSIO vs. Usher - Yeah Nuttööö", artist: "Daniel Hein Mashups", plays: "" }
      ]
    };

    // لتتبع حالة التحميل
    let isLoading = false;
    let currentLang = 'ku';
    const loadingBar = document.getElementById('loading-bar');

    function startLoading() {
      if (isLoading) return;
      isLoading = true;
      loadingBar.style.width = '20%';
      
      // محاكاة تحميل تدريجي
      setTimeout(() => { if (isLoading) loadingBar.style.width = '50%'; }, 300);
      setTimeout(() => { if (isLoading) loadingBar.style.width = '80%'; }, 600);
    }

    function stopLoading() {
      isLoading = false;
      loadingBar.style.width = '100%';
      setTimeout(() => { loadingBar.style.width = '0%'; }, 500);
    }

    function load(lang) {
      currentLang = lang;
      const playerBox = document.getElementById('player-box');
      const trackList = document.getElementById('track-list');
      
      // إظهار شريط التحميل
      startLoading();
      
      // تحميل المشغل
      if (players[lang]) {
        // في أندرويد، نستخدم خدعة للتشغيل التلقائي
        if (/Android/i.test(navigator.userAgent)) {
          // ننتظر تفاعل المستخدم أولاً
          setTimeout(() => {
            playerBox.innerHTML = `<iframe src="${players[lang]}" allow="autoplay; encrypted-media" allowtransparency="true" frameborder="no" scrolling="no"></iframe>`;
            stopLoading();
          }, 100);
        } else {
          // للمتصفحات الأخرى
          playerBox.innerHTML = `<iframe src="${players[lang]}" allow="autoplay; encrypted-media" allowtransparency="true" frameborder="no" scrolling="no"></iframe>`;
          stopLoading();
        }
      } else {
        playerBox.innerHTML = "<p style='color: #888; padding: 20px;'>المشغل غير متوفر.</p>";
        stopLoading();
      }

      // تحميل قائمة الأغاني
      if (tracks[lang] && tracks[lang].length > 0) {
        const listHTML = tracks[lang].map(track => 
          `<div class="track-item">
            <div class="track-title">${track.title}</div>
            <div class="track-artist">${track.artist}</div>
            ${track.plays ? `<div class="track-stats">${track.plays} تشغيلاً</div>` : ''}
          </div>`
        ).join('');
        trackList.innerHTML = `<div class="track-list"><h3>قائمة الأغاني</h3>${listHTML}</div>`;
      } else {
        trackList.innerHTML = "<p style='color: #888; padding: 10px;'>قائمة الأغاني غير متوفرة.</p>";
      }
      
      // تحديث مؤشر الحالة
      document.querySelector('.status-indicator').style.background = '#4CAF50';
    }

    // تحميل اللغة الكردية افتراضيًا مع رسالة توضيحية
    window.onload = () => {
      // في أندرويد، نعرض رسالة توضيحية أولاً
      if (/Android/i.test(navigator.userAgent)) {
        document.getElementById('player-box').innerHTML = 
          `<div style="padding: 30px 15px; color: #666; background: #fff; border-radius: 16px; margin: 10px;">
            <p style="margin: 0 0 15px;">للحصول على أفضل تجربة:</p>
            <p style="margin: 0 0 15px; font-weight: bold;">اضغط على زر اللغة لبدء التشغيل</p>
            <p style="margin: 0; font-size: 0.9rem; color: #777;">(ملاحظة: بعض متصفحات أندرويد تتطلب تفاعلاً من المستخدم قبل التشغيل التلقائي)</p>
          </div>`;
          
        // تحميل اللغة الكردية كخلفية (بدون عرض)
        const tempDiv = document.createElement('div');
        tempDiv.style.display = 'none';
        tempDiv.innerHTML = `<iframe src="${players.ku}"></iframe>`;
        document.body.appendChild(tempDiv);
      } else {
        load('ku');
      }
    };

    // لتحسين تجربة التشغيل على أندرويد
    document.addEventListener('touchstart', function() {
      if (!isLoading && currentLang) {
        // إعادة تحميل المشغل عند أول تفاعل
        load(currentLang);
      }
    }, { passive: true });
  </script>

</body>
</html>
