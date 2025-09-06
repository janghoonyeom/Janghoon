# Janghoon
<!DOCTYPE html>
<html lang="ko">
<head><meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0"><title>내 첫 사이트</title></head>
<body><h1>안녕하세요!</h1><p>모바일에서도 잘 보입니다.</p></body>
</html>
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>다국어 지원 사이트</title>
  <style>
    body { font-family: sans-serif; text-align: center; padding: 40px; }
    .lang-btn { margin: 5px; padding: 8px 15px; border: none; border-radius: 6px; cursor: pointer; }
    .lang-btn:hover { opacity: 0.8; }
    #content { margin-top: 30px; font-size: 1.2em; }
  </style>
</head>
<body>
  <h1 id="title">안녕하세요 👋</h1>
  <p id="content">이 사이트는 다국어를 지원합니다.</p>

  <!-- 언어 선택 버튼 -->
  <div>
    <button class="lang-btn" onclick="setLang('ko')">한국어</button>
    <button class="lang-btn" onclick="setLang('en')">English</button>
    <button class="lang-btn" onclick="setLang('th')">ไทย</button>
  </div>

  <script>
    const translations = {
      ko: {
        title: "안녕하세요 👋",
        content: "이 사이트는 다국어를 지원합니다."
      },
      en: {
        title: "Hello 👋",
        content: "This site supports multiple languages."
      },
      th: {
        title: "สวัสดีครับ 👋",
        content: "เว็บไซต์นี้รองรับหลายภาษา"
      }
    };

    function setLang(lang) {
      document.getElementById("title").innerText = translations[lang].title;
      document.getElementById("content").innerText = translations[lang].content;
    }
  </script>
</body>
</html>
