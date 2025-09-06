<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pro-Ventures 관리</title>
  <style>
    body { margin: 0; font-family: "Noto Sans KR", sans-serif; background: #f9f9f9; }
    header { background: #222; color: #fff; padding: 10px; text-align: right; font-size: 14px; }
    header span { margin-left: 20px; cursor: pointer; }
    .logo-bar { background: #fff; padding: 15px; text-align: center; border-bottom: 2px solid #ddd; }
    .logo-bar h1 { margin: 0; font-size: 20px; }
    nav { background: #c00; display: flex; justify-content: center; }
    nav a { color: #fff; padding: 12px 15px; text-decoration: none; font-weight: bold; }
    nav a.active { background: #900; }
    .submenu { background: #333; color: #fff; display: flex; justify-content: center; }
    .submenu a { padding: 10px 12px; color: #fff; text-decoration: none; font-size: 13px; }
    .submenu a:hover { text-decoration: underline; }
    main { padding: 20px; }
    h2 { margin-top: 0; }
    .summary { display: flex; gap: 20px; margin-bottom: 20px; }
    .summary div { background: #fff; padding: 15px; border-radius: 6px; flex: 1; box-shadow: 0 2px 5px rgba(0,0,0,0.1); text-align: center; }
    table { width: 100%; border-collapse: collapse; background: #fff; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
    th, td { border: 1px solid #ddd; padding: 10px; text-align: center; }
    th { background: #f1f1f1; }
    footer { text-align: center; font-size: 13px; padding: 15px; color: #666; }
  </style>
</head>
<body>

  <!-- 상단 헤더 -->
  <header>
    메시지 4건 있습니다. 
    <span>마이페이지</span> 
    <span>로그아웃</span>
  </header>

  <!-- 로고 -->
  <div class="logo-bar">
    <h1>PRO-VENTURES</h1>
    <p>동대문, 남대문 전문 사입팀</p>
  </div>

  <!-- 메인 메뉴 -->
  <nav>
    <a href="#" class="active">주문</a>
    <a href="#">사입내역</a>
    <a href="#">사입완료</a>
    <a href="#">정산</a>
    <a href="#">추가</a>
    <a href="#">교환확인</a>
  </nav>

  <!-- 서브 메뉴 -->
  <div class="submenu">
    <a href="#">거래처정보</a>
    <a href="#">매장검색</a>
    <a href="#">삼촌내역</a>
    <a href="#">거래처내역</a>
    <a href="#">주문검색</a>
    <a href="#">주문등록</a>
    <a href="#">카톡전송</a>
  </div>

  <!-- 본문 -->
  <main>
    <h2>주문 현황</h2>
    <div class="summary">
      <div><strong>동대문</strong><br>접수: 84 / 대기: 0</div>
      <div><strong>남대문</strong><br>접수: 0 / 대기: 0</div>
    </div>

    <!-- 주문 테이블 -->
    <table>
      <thead>
        <tr>
          <th>번호</th>
          <th>상가</th>
          <th>접수</th>
          <th>대기</th>
        </tr>
      </thead>
      <tbody>
        <tr><td>1</td><td>테크노</td><td>25</td><td>0</td></tr>
        <tr><td>2</td><td>디오트</td><td>12</td><td>0</td></tr>
        <tr><td>3</td><td>APM</td><td>12</td><td>0</td></tr>
        <tr><td>4</td><td>남평화</td><td>9</td><td>0</td></tr>
        <tr><td>5</td><td>뉴존</td><td>8</td><td>0</td></tr>
      </tbody>
    </table>
  </main>

  <footer>
    © 2025 Pro-Ventures. All rights reserved.
  </footer>

</body>
</html>
