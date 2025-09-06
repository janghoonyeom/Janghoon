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
    nav { background: #c00; display: flex; justify-content: center; flex-wrap: wrap; }
    nav a { color: #fff; padding: 12px 15px; text-decoration: none; font-weight: bold; cursor: pointer; }
    nav a.active { background: #900; }
    main { padding: 20px; }
    h2 { margin-top: 0; }
    .summary { display: flex; gap: 20px; margin-bottom: 20px; flex-wrap: wrap; }
    .summary div { background: #fff; padding: 15px; border-radius: 6px; flex: 1; box-shadow: 0 2px 5px rgba(0,0,0,0.1); text-align: center; min-width: 120px; }
    table { width: 100%; border-collapse: collapse; background: #fff; box-shadow: 0 2px 5px rgba(0,0,0,0.1); margin-bottom: 20px; }
    th, td { border: 1px solid #ddd; padding: 10px; text-align: center; }
    th { background: #f1f1f1; }
    footer { text-align: center; font-size: 13px; padding: 15px; color: #666; }
    .lang-box { text-align: center; margin: 10px 0; }
    .lang-btn { margin: 3px; padding: 6px 12px; border: none; border-radius: 6px; cursor: pointer; }
    .lang-btn:hover { opacity: 0.8; }
  </style>
</head>
<body>

  <!-- 상단 헤더 -->
  <header>
    <span id="msg">메시지 4건 있습니다.</span>
    <span id="mypage">마이페이지</span> 
    <span id="logout">로그아웃</span>
  </header>

  <!-- 로고 -->
  <div class="logo-bar">
    <h1>PRO-VENTURES</h1>
    <p id="slogan">동대문, 남대문 전문 사입팀</p>
  </div>

  <!-- 언어 선택 -->
  <div class="lang-box">
    <button class="lang-btn" onclick="setLang('ko')">한국어</button>
    <button class="lang-btn" onclick="setLang('en')">English</button>
    <button class="lang-btn" onclick="setLang('th')">ไทย</button>
  </div>

  <!-- 메인 메뉴 -->
  <nav>
    <a id="menuOrder" class="active" onclick="showPage('order')">주문</a>
    <a id="menuSettle" onclick="showPage('settle')">정산</a>
  </nav>

  <!-- 본문 -->
  <main>
    <!-- 주문 화면 -->
    <section id="orderPage">
      <h2 id="orderTitle">주문 현황</h2>
      <div class="summary">
        <div><strong id="dongdaemun">동대문</strong><br><span id="dongStatus">접수: 84 / 대기: 0</span></div>
        <div><strong id="namdaemun">남대문</strong><br><span id="namStatus">접수: 0 / 대기: 0</span></div>
      </div>
      <table>
        <thead>
          <tr>
            <th id="thNo">번호</th>
            <th id="thStore">상가</th>
            <th id="thAccept">접수</th>
            <th id="thWait">대기</th>
          </tr>
        </thead>
        <tbody id="orderTable">
          <tr><td>1</td><td>테크노</td><td>25</td><td>0</td></tr>
          <tr><td>2</td><td>디오트</td><td>12</td><td>0</td></tr>
          <tr><td>3</td><td>APM</td><td>12</td><td>0</td></tr>
          <tr><td>4</td><td>남평화</td><td>9</td><td>0</td></tr>
          <tr><td>5</td><td>뉴존</td><td>8</td><td>0</td></tr>
        </tbody>
      </table>
    </section>

    <!-- 정산 화면 -->
    <section id="settlePage" style="display:none;">
      <h2 id="settleTitle">정산</h2>

      <!-- 매장별 합계 -->
      <table>
        <thead>
          <tr>
            <th id="stStore">상가</th>
            <th id="stTotal">총 매출</th>
          </tr>
        </thead>
        <tbody id="settleTable"></tbody>
        <tfoot>
          <tr>
            <th id="stSum">합계</th>
            <th id="settleSum">0</th>
          </tr>
        </tfoot>
      </table>

      <!-- 결제수단별 합계 -->
      <h3 id="paymentTitle">결제수단별 합계</h3>
      <table>
        <thead>
          <tr>
            <th id="payMethod">결제수단</th>
            <th id="payAmount">금액</th>
          </tr>
        </thead>
        <tbody id="paymentTable"></tbody>
      </table>
    </section>
  </main>

  <footer>
    © 2025 Pro-Ventures. All rights reserved.
  </footer>

  <script>
    // 샘플 주문 데이터 (매장별, 결제수단 포함)
    const orders = [
      { store: "테크노", sales: 25, method: "현금" },
      { store: "디오트", sales: 12, method: "카드" },
      { store: "APM", sales: 12, method: "이체" },
      { store: "남평화", sales: 9, method: "현금" },
      { store: "뉴존", sales: 8, method: "카드" }
    ];

    // 화면 전환
    function showPage(page) {
      document.getElementById("orderPage").style.display = (page === "order") ? "block" : "none";
      document.getElementById("settlePage").style.display = (page === "settle") ? "block" : "none";

      document.getElementById("menuOrder").classList.toggle("active", page === "order");
      document.getElementById("menuSettle").classList.toggle("active", page === "settle");

      if (page === "settle") showSettlement();
    }

    // 정산 데이터 계산
    function showSettlement() {
      // 매장별 합계
      const tbody = document.getElementById("settleTable");
      tbody.innerHTML = "";
      let total = 0;
      orders.forEach(o => {
        const tr = document.createElement("tr");
        tr.innerHTML = `<td>${o.store}</td><td>${o.sales}</td>`;
        tbody.appendChild(tr);
        total += o.sales;
      });
      document.getElementById("settleSum").innerText = total;

      // 결제수단별 합계
      const paySummary = {};
      orders.forEach(o => {
        paySummary[o.method] = (paySummary[o.method] || 0) + o.sales;
      });
      const payBody = document.getElementById("paymentTable");
      payBody.innerHTML = "";
      for (let method in paySummary) {
        const tr = document.createElement("tr");
        tr.innerHTML = `<td>${method}</td><td>${paySummary[method]}</td>`;
        payBody.appendChild(tr);
      }
    }

    // 다국어 데이터
    const translations = {
      ko: {
        msg: "메시지 4건 있습니다.",
        mypage: "마이페이지",
        logout: "로그아웃",
        slogan: "동대문, 남대문 전문 사입팀",
        menuOrder: "주문",
        menuSettle: "정산",
        orderTitle: "주문 현황",
        thNo: "번호", thStore: "상가", thAccept: "접수", thWait: "대기",
        settleTitle: "정산", stStore: "상가", stTotal: "총 매출", stSum: "합계",
        paymentTitle: "결제수단별 합계", payMethod: "결제수단", payAmount: "금액"
      },
      en: {
        msg: "You have 4 new messages.",
        mypage: "My Page",
        logout: "Logout",
        slogan: "Dongdaemun & Namdaemun Wholesale Team",
        menuOrder: "Orders",
        menuSettle: "Settlement",
        orderTitle: "Order Status",
        thNo: "No", thStore: "Store", thAccept: "Accepted", thWait: "Pending",
        settleTitle: "Settlement", stStore: "Store", stTotal: "Total Sales", stSum: "Sum",
        paymentTitle: "Payment Summary", payMethod: "Method", payAmount: "Amount"
      },
      th: {
        msg: "คุณมีข้อความใหม่ 4 ข้อความ",
        mypage: "หน้าของฉัน",
        logout: "ออกจากระบบ",
        slogan: "ทีมสั่งซื้อ ดงแดมุน และนัมแดมุน",
        menuOrder: "ออเดอร์",
        menuSettle: "การชำระบัญชี",
        orderTitle: "สถานะออเดอร์",
        thNo: "ลำดับ", thStore: "ร้าน", thAccept: "รับแล้ว", thWait: "รอ",
        settleTitle: "การชำระบัญชี", stStore: "ร้าน", stTotal: "ยอดขายรวม", stSum: "รวม",
        paymentTitle: "สรุปตามวิธีการชำระเงิน", payMethod: "วิธีการ", payAmount: "จำนวนเงิน"
      }
    };

    function setLang(lang) {
      const t = translations[lang];
      for (let key in t) {
        const el = document.getElementById(key);
        if (el) el.innerText = t[key];
      }
    }
  </script>
</body>
</html>
