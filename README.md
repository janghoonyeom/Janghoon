<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>다국어 매장 관리</title>
  <style>
    body { font-family: sans-serif; text-align: center; padding: 20px; }
    h1 { margin-bottom: 10px; }
    .lang-btn { margin: 5px; padding: 6px 12px; border: none; border-radius: 6px; cursor: pointer; }
    .lang-btn:hover { opacity: 0.8; }
    .filter-box { margin: 20px 0; }
    select, input { padding: 6px; margin: 5px; }
    table { width: 100%; border-collapse: collapse; margin-top: 20px; }
    th, td { border: 1px solid #ccc; padding: 8px; text-align: center; }
    th { background: #f5f5f5; }
  </style>
</head>
<body>
  <h1 id="title">안녕하세요 👋</h1>
  <p id="desc">이 사이트는 다국어, 날짜 선택, 매장 필터를 지원합니다.</p>

  <!-- 언어 선택 -->
  <div>
    <button class="lang-btn" onclick="setLang('ko')">한국어</button>
    <button class="lang-btn" onclick="setLang('en')">English</button>
    <button class="lang-btn" onclick="setLang('th')">ไทย</button>
  </div>

  <!-- 날짜 선택 + 매장 필터 -->
  <div class="filter-box">
    <label id="dateLabel">날짜 선택: </label>
    <input type="date" id="dateFilter">

    <label id="storeLabel">매장 선택: </label>
    <select id="storeFilter">
      <option value="all">전체</option>
      <option value="storeA">매장 A</option>
      <option value="storeB">매장 B</option>
      <option value="storeC">매장 C</option>
    </select>

    <
