[taiwan_support_group_v2.index.html](https://github.com/user-attachments/files/27149771/taiwan_support_group_v2.index.html)
<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>台灣病友團體搜尋引擎</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+TC:wght@400;700&family=Noto+Sans+TC:wght@300;400;500;700&display=swap" rel="stylesheet">

<style>
  :root {
    --bg: #f0e8de;
    --card-bg: #ede4da;
    --border: #b8956a;
    --border-light: #c9a882;
    --text: #2c1f0f;
    --text-muted: #6b4f35;
    --accent: #c9a882;
    --btn-bg: #c9a882;
    --btn-text: #2c1f0f;
    --purple: #7c6ea0;
    --purple-light: #b3a8c8;
    --nav-bg: #ede4da;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { background: var(--bg); font-family: 'Noto Sans TC', sans-serif; color: var(--text); min-height: 100vh; max-width: 640px; margin: 0 auto; }
  nav { display: flex; justify-content: center; gap: 8px; padding: 12px 14px; background: var(--nav-bg); flex-wrap: wrap; position: sticky; top: 0; z-index: 100; border-bottom: 1px solid var(--border-light); }
  nav a { padding: 5px 14px; border: 1.5px solid var(--border); border-radius: 20px; font-size: 13px; color: var(--text); cursor: pointer; text-decoration: none; background: transparent; transition: background 0.2s; }
  nav a:hover, nav a.active { background: var(--accent); }
  .page { display: none; padding-bottom: 40px; }
  .page.active { display: block; }

  /* HERO */
  .hero { margin: 14px; border: 2.5px solid var(--purple); border-radius: 8px; display: flex; align-items: stretch; overflow: hidden; background: var(--card-bg); min-height: 140px; }
  .hero-text { padding: 18px 14px; flex: 1; }
  .hero-text h1 { font-family: 'Noto Serif TC', serif; font-size: 22px; font-weight: 700; line-height: 1.4; margin-bottom: 8px; }
  .hero-text p { font-size: 11px; font-weight: 700; color: var(--text-muted); line-height: 1.7; text-transform: uppercase; letter-spacing: 0.3px; }
  .hero-img { width: 150px; flex-shrink: 0; background: linear-gradient(135deg, #c9b99a, #a8896a); display: flex; align-items: center; justify-content: center; font-size: 56px; }

  /* SEARCH */
  .search-section { padding: 14px 14px 8px; }
  .section-title { font-family: 'Noto Serif TC', serif; font-size: 17px; font-weight: 700; margin-bottom: 2px; }
  .section-sub { font-size: 10px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: var(--text-muted); margin-bottom: 16px; }

  .search-row { display: flex; align-items: center; gap: 8px; margin-bottom: 8px; }
  .search-row .row-label { display: flex; flex-direction: column; align-items: flex-start; font-size: 14px; font-weight: 500; min-width: 50px; line-height: 1.3; flex-shrink: 0; }
  .search-row .row-label span { font-size: 9px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: var(--text-muted); }
  .search-row select, .search-row input {
    flex: 1; height: 34px; border: 1.5px solid var(--border); border-radius: 20px;
    background: transparent; padding: 0 14px; font-size: 13px; font-family: 'Noto Sans TC', sans-serif;
    color: var(--text); outline: none; appearance: none; -webkit-appearance: none;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%236b4f35' d='M6 8L1 3h10z'/%3E%3C/svg%3E");
    background-repeat: no-repeat; background-position: right 12px center; padding-right: 30px;
  }
  .search-row select:focus, .search-row input:focus { border-color: var(--purple); }
  .or-divider { text-align: center; font-weight: 700; font-size: 13px; margin: 6px 0; color: var(--text); }
  .tw-deco { position: absolute; right: 8px; top: 50%; transform: translateY(-50%); display: flex; flex-direction: column; align-items: center; gap: 6px; opacity: 0.28; pointer-events: none; font-size: 28px; }
  .search-area { position: relative; padding-right: 50px; }
  #other-disease-row { display: none; }

  .submit-btn { display: block; margin: 16px auto 0; padding: 7px 28px; background: var(--btn-bg); color: var(--btn-text); border: 1.5px solid var(--border); border-radius: 20px; font-size: 14px; font-family: 'Noto Sans TC', sans-serif; font-weight: 500; cursor: pointer; transition: background 0.2s; }
  .submit-btn:hover { background: var(--border); }


  /* MAP */
  .location-section { padding: 14px; }
  .map-embed { width: 100%; height: 200px; border: 1.5px solid var(--border); border-radius: 8px; overflow: hidden; position: relative; }
  .map-embed iframe { width: 100%; height: 100%; border: none; }
  .map-placeholder { width: 100%; height: 200px; background: #e8ddd0; border: 1.5px solid var(--border); border-radius: 8px; display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 8px; color: var(--text-muted); font-size: 13px; }
  .map-placeholder .icon { font-size: 32px; }
  .loc-btn { padding: 6px 18px; background: var(--btn-bg); border: 1.5px solid var(--border); border-radius: 20px; font-size: 12px; font-family: 'Noto Sans TC', sans-serif; color: var(--text); cursor: pointer; }

  /* RESOURCES */
  .resources-section { padding: 14px; }
  .resources-divider { height: 1.5px; background: var(--border-light); margin-bottom: 12px; }
  .resource-item { margin-bottom: 10px; }
  .resource-item .r-label { font-size: 13px; font-weight: 700; margin-bottom: 2px; }
  .resource-item a { font-size: 10px; font-weight: 700; letter-spacing: 0.3px; text-transform: uppercase; color: var(--text-muted); word-break: break-all; text-decoration: none; }
  .resource-item a:hover { text-decoration: underline; }

  /* RESULTS */
  .results-section { padding: 14px; }
  .results-layout { display: flex; gap: 12px; align-items: flex-start; }
  .result-list-col { flex: 1; }
  .result-map-col { width: 44%; }
  .result-map-col .map-embed { height: 170px; }
  .result-list { list-style: none; }
  .result-list li { margin-bottom: 12px; font-size: 14px; font-weight: 500; }
  .result-list li a { color: var(--text); text-decoration: underline; cursor: pointer; }
  .result-list li.highlight a { color: var(--purple); font-weight: 700; }
  .result-list li .num { font-weight: 700; margin-right: 3px; }

  /* DETAIL */
  .detail-section { padding: 14px; }
  .group-name-tag { display: inline-block; background: var(--btn-bg); border: 1.5px solid var(--border); border-radius: 20px; padding: 5px 16px; font-size: 14px; font-weight: 700; margin-bottom: 12px; }
  .detail-layout { display: flex; gap: 12px; margin-bottom: 12px; }
  .detail-info { flex: 1; }
  .detail-info-row { display: flex; align-items: flex-start; gap: 7px; margin-bottom: 9px; font-size: 12px; font-weight: 500; }
  .detail-info-row .icon { font-size: 15px; flex-shrink: 0; margin-top: 1px; }
  .detail-map-col { width: 44%; }
  .detail-map-col .map-embed { height: 170px; }
  .tags-row { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 16px; }
  .tag { padding: 3px 12px; border: 1.5px solid var(--border); border-radius: 20px; font-size: 11px; font-weight: 500; }
  .divider { border: none; border-top: 1.5px solid var(--border-light); margin: 14px 0; }

  /* FORMS */
  .contact-title { text-align: center; font-size: 14px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 16px; }
  .form-row { display: flex; align-items: center; margin-bottom: 9px; gap: 10px; }
  .form-row label { display: flex; flex-direction: column; align-items: flex-end; min-width: 68px; font-size: 12px; font-weight: 500; line-height: 1.3; flex-shrink: 0; }
  .form-row label span { font-size: 9px; font-weight: 700; letter-spacing: 1px; text-transform: uppercase; color: var(--text-muted); }
  .form-row input, .form-row textarea {
    flex: 1; border: 1.5px solid var(--border); border-radius: 20px;
    background: transparent; padding: 7px 14px;
    font-size: 13px; font-family: 'Noto Sans TC', sans-serif; color: var(--text); outline: none;
  }
  .form-row textarea { border-radius: 10px; resize: vertical; min-height: 56px; }
  .form-row input:focus, .form-row textarea:focus { border-color: var(--purple); }

  /* SHARE PAGE */
  .share-banner { margin: 14px; background: var(--card-bg); border-radius: 8px; border: 1px solid var(--border-light); overflow: hidden; }
  .share-section { padding: 0 14px 14px; }
  .share-title { text-align: center; font-family: 'Noto Serif TC', serif; font-size: 20px; font-weight: 700; margin-bottom: 2px; }
  .share-sub { text-align: center; font-size: 10px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: var(--text-muted); margin-bottom: 16px; }

  /* JOIN */
  .join-title { text-align: center; font-family: 'Noto Serif TC', serif; font-size: 22px; font-weight: 700; padding: 20px 14px 16px; }

  /* CONTACT BOX */
  .contact-box { margin: 14px; border: 2.5px solid var(--purple); border-radius: 8px; padding: 18px 14px; background: var(--card-bg); }

  /* TOAST */
  .success-toast { display: none; background: #c9a882; color: #2c1f0f; border-radius: 8px; padding: 9px 16px; text-align: center; font-weight: 500; margin: 9px 14px 0; font-size: 13px; }


</style>
</head>
<body>

<nav>
  <a onclick="showPage('home')" class="active" id="nav-home">首頁</a>
  <a onclick="showPage('share')" id="nav-share">心得分享</a>
  <a onclick="showPage('contact')" id="nav-contact">聯絡我們</a>
  <a onclick="showPage('pro')" id="nav-pro">專業團體</a>
</nav>

<!-- ===================== PAGE 1: 首頁 ===================== -->
<div class="page active" id="page-home">
  <div class="hero">
    <div class="hero-text">
      <h1>台灣病友團體搜尋引擎</h1>
      <p>Taiwan-Based Community Support<br>Group Finder</p>
    </div>
    <div class="hero-img">🤝</div>
  </div>

  <div class="search-section">
    <div class="section-title">請輸入....</div>
    <div class="section-sub">PLEASE ENTER...</div>
    <div class="search-area">
      <div class="search-row">
        <div class="row-label">縣市<span>CITY</span></div>
        <select id="city-select">
          <option value="">請選擇縣市...</option>
          <option>臺北市</option><option>新北市</option><option>桃園市</option>
          <option>臺中市</option><option>臺南市</option><option>高雄市</option>
          <option>基隆市</option><option>新竹市</option><option>新竹縣</option>
          <option>苗栗縣</option><option>彰化縣</option><option>南投縣</option>
          <option>雲林縣</option><option>嘉義市</option><option>嘉義縣</option>
          <option>屏東縣</option><option>宜蘭縣</option><option>花蓮縣</option>
          <option>臺東縣</option><option>澎湖縣</option><option>金門縣</option><option>連江縣</option>
        </select>
        <div class="row-label" style="min-width:16px;align-items:center;">區</div>
        <input type="text" id="district-input" placeholder="">
      </div>
      <div class="or-divider">OR</div>
      <div class="search-row">
        <div class="row-label">醫院<span>HOSPITAL</span></div>
        <select id="hospital-select">
          <option value="">請選擇醫院...</option>
          <option>台北榮總</option>
          <option>台大醫院</option>
          <option>臺北醫學大學附屬醫院</option>
          <option>三軍總醫院</option>
        </select>
      </div>
      <div class="or-divider">OR</div>
      <div class="search-row">
        <div class="row-label">診斷<span>DISEASE</span></div>
        <select id="disease-select" onchange="toggleOtherDisease(this)">
          <option value="">請選擇診斷...</option>
          <option>中風</option>
          <option>TBI（腦部創傷）</option>
          <option>SCI（脊髓損傷）</option>
          <option>職業災害</option>
          <option>車禍</option>
          <option>其他</option>
        </select>
      </div>
      <div class="search-row" id="other-disease-row">
        <div class="row-label">其他<span>OTHER</span></div>
        <input type="text" id="other-disease-input" placeholder="請輸入疾病名稱">
      </div>
      <div class="tw-deco"><span>🗺️</span><span>🏙️</span></div>
    </div>
    <button class="submit-btn" onclick="doSearch()">送出</button>
  </div>

  <div class="location-section">
    <div class="section-title" style="margin-bottom:2px;">你的位置</div>
    <div class="section-sub">YOUR LOCATION</div>
    <div id="map-container">
      <div class="map-placeholder" id="map-placeholder">
        <div class="icon">📍</div>
        <div>點擊以取得您的目前位置</div>
        <button class="loc-btn" onclick="getLocation()">📍 取得目前位置</button>
      </div>
      <div id="map-frame" style="display:none;" class="map-embed"></div>
    </div>
  </div>

  <div class="resources-section">
    <div class="section-title">線上資源 <span style="font-size:11px;font-weight:700;letter-spacing:2px;text-transform:uppercase;color:var(--text-muted);">ONLINE RESOURSES</span></div>
    <div class="resources-divider"></div>
    <div class="resource-item"><div class="r-label">單手廚房：</div><a href="https://singlehandkitchen.medium.com" target="_blank">HTTPS://SINGLEHANDKITCHEN.MEDIUM.COM</a></div>
    <div class="resource-item"><div class="r-label">腦中風復健照護交流FB：</div><a href="https://www.facebook.com/groups/stroke.rehab/" target="_blank">HTTPS://WWW.FACEBOOK.COM/GROUPS/STROKE.REHAB/?REF=SHARE&MIBEXTID=WWXIFR&RDID=CR0YMXDLDN9D4ACP</a></div>
    <div class="resource-item" style="margin-top:8px;"><div class="r-label">台灣腦中風關懷協會FB：</div><a href="https://www.facebook.com/taiwanstrokeassociation" target="_blank">HTTPS://WWW.FACEBOOK.COM/TAIWANSTROKEASSOCIATION</a></div>
    <div class="resource-item" style="margin-top:8px;"><div class="r-label">腦中風復健照護交流 LINE OPENCHAT:</div><a href="https://openchat.line.me/tw/cover/ssxxcoawqqt5qvdoh5-vzzqneoyoebakzng2tuoxapfyi4ntcuuy8lmk4am" target="_blank">HTTPS://OPENCHAT.LINE.ME/TW/COVER/SSXXCOAWQQT5QVDOH5-VZZQNEOYOEBAKZNG2TUOXAPFYI4NTCUUY8LMK4AM</a></div>
  </div>
</div>

<!-- ===================== PAGE 2: 搜尋結果 ===================== -->
<div class="page" id="page-results">
  <div class="results-section">
    <div class="section-title">搜尋結果....</div>
    <div class="section-sub">RESULTS...</div>
    <div class="results-layout">
      <div class="result-list-col">
        <ul class="result-list">
          <li class="highlight"><span class="num">1.</span><a onclick="showPage('detail')">台北榮總腦中風病友會</a></li>
          <li><span class="num">2.</span><a onclick="showPage('detail')">台北醫學大學附設醫院 復健支持團體</a></li>
          <li><span class="num">3.</span><a onclick="showPage('detail')">馬偕紀念醫院 中風病友會</a></li>
        </ul>
      </div>
      <div class="result-map-col">
        <div class="map-embed">
          <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d28893!2d121.513!3d25.063!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3442a96248f82a4d%3A0x8a3e01f924a2a8a3!2sTaipei+Veterans+General+Hospital!5e0!3m2!1szh-TW!2stw!4v1" allowfullscreen loading="lazy"></iframe>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ===================== PAGE 3: 團體詳情 ===================== -->
<div class="page" id="page-detail">
  <div class="detail-section">
    <div class="group-name-tag">臺北榮總腦中風病友會</div>
    <div class="detail-layout">
      <div class="detail-info">
        <div class="detail-info-row"><span class="icon">📞</span><span>(02)28712121 #86693、86694</span></div>
        <div class="detail-info-row"><span class="icon">📍</span><span>11217臺北市北投區石牌路二段201號</span></div>
        <div class="detail-info-row"><span class="icon">文A</span><span>中文／台語</span></div>
        <div class="detail-info-row"><span class="icon">🕐</span><span>不定期團體　資訊分享、病友交流</span></div>
      </div>
      <div class="detail-map-col">
        <div class="map-embed">
          <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3612!2d121.513!3d25.064!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3442a96248f82a4d%3A0x8a3e01f924a2a8a3!2sTaipei+Veterans+General+Hospital!5e0!3m2!1szh-TW!2stw!4v1" allowfullscreen loading="lazy"></iframe>
        </div>
      </div>
    </div>
    <div class="tags-row">
      <span class="tag">腦中風</span><span class="tag">榮總</span><span class="tag">台北榮總</span><span class="tag">北投區</span><span class="tag">石牌捷運站</span>
    </div>
    <hr class="divider">
    <div class="contact-title">CONTACT US</div>
    <form id="form-detail" onsubmit="submitForm(event,'detail')">
      <div class="form-row"><label>姓名<span>NAME</span></label><input type="text" id="d-name" required></div>
      <div class="form-row"><label>聯繫電話<span>PHONE</span></label><input type="tel" id="d-phone"></div>
      <div class="form-row"><label>電子信箱<span>EMAIL</span></label><input type="email" id="d-email"></div>
      <div class="form-row"><label>備注<span>COMMENT</span></label><textarea id="d-comment"></textarea></div>
      <button type="submit" class="submit-btn">送出</button>
    </form>
    <div class="success-toast" id="toast-detail">感謝您的留言！已成功送出。</div>
  </div>
</div>

<!-- ===================== PAGE 4: 心得分享 ===================== -->
<div class="page" id="page-share">
  <div class="share-banner">
    <svg viewBox="0 0 320 120" width="100%" xmlns="http://www.w3.org/2000/svg">
      <g fill="#b3a8c8" opacity="0.65">
        <circle cx="28" cy="58" r="10"/><rect x="20" y="69" width="16" height="24" rx="5"/>
        <circle cx="72" cy="44" r="10"/><rect x="64" y="55" width="16" height="24" rx="5"/>
        <circle cx="135" cy="64" r="10"/><rect x="127" y="75" width="16" height="24" rx="5"/>
        <circle cx="192" cy="48" r="10"/><rect x="184" y="59" width="16" height="24" rx="5"/>
        <circle cx="248" cy="60" r="10"/><rect x="240" y="71" width="16" height="24" rx="5"/>
        <circle cx="294" cy="42" r="10"/><rect x="286" y="53" width="16" height="24" rx="5"/>
      </g>
      <g fill="none" stroke="#b3a8c8" stroke-width="2" opacity="0.55">
        <rect x="40" y="16" width="38" height="28" rx="7"/><polyline points="47,44 41,54"/>
        <line x1="48" y1="26" x2="66" y2="26"/><line x1="48" y1="32" x2="66" y2="32"/>
        <rect x="93" y="6" width="38" height="28" rx="7"/><polyline points="100,34 94,44"/>
        <line x1="101" y1="16" x2="119" y2="16"/><line x1="101" y1="22" x2="119" y2="22"/>
        <rect x="150" y="14" width="38" height="28" rx="7"/><polyline points="157,42 151,52"/>
        <line x1="158" y1="24" x2="176" y2="24"/><line x1="158" y1="30" x2="176" y2="30"/>
        <rect x="207" y="8" width="38" height="28" rx="7"/><polyline points="214,36 208,46"/>
        <line x1="215" y1="18" x2="233" y2="18"/><line x1="215" y1="24" x2="233" y2="24"/>
        <rect x="258" y="18" width="38" height="28" rx="7"/><polyline points="265,46 259,56"/>
        <line x1="266" y1="28" x2="284" y2="28"/><line x1="266" y1="34" x2="284" y2="34"/>
      </g>
    </svg>
  </div>
  <div class="share-section">
    <div class="share-title">我要投稿</div>
    <div class="share-sub">SHARE MY THOUGHTS</div>
    <form id="form-share" onsubmit="submitForm(event,'share')">
      <div class="form-row"><label>姓名<span>NAME</span></label><input type="text" id="s-name" required></div>
      <div class="form-row"><label>聯繫電話<span>PHONE</span></label><input type="tel" id="s-phone"></div>
      <div class="form-row"><label>電子信箱<span>EMAIL</span></label><input type="email" id="s-email"></div>
      <div class="form-row"><label>我要說…<span>COMMENT</span></label><textarea id="s-comment"></textarea></div>
      <button type="submit" class="submit-btn">送出</button>
    </form>
    <div class="success-toast" id="toast-share">感謝您的投稿！已成功送出。</div>
  </div>
</div>

<!-- ===================== PAGE 5: 專業團體 ===================== -->
<div class="page" id="page-pro">
  <div class="join-title">我要加入</div>
  <div style="padding: 0 14px 14px;">
    <form id="form-pro" onsubmit="submitForm(event,'pro')">
      <div class="form-row"><label>團體名稱<span>GROUP NAME</span></label><input type="text" id="p-name" required></div>
      <div class="form-row"><label>聯繫電話<span>PHONE</span></label><input type="tel" id="p-phone"></div>
      <div class="form-row"><label>電子信箱<span>EMAIL</span></label><input type="email" id="p-email"></div>
      <div class="form-row"><label>備註<span>COMMENT</span></label><input type="text" id="p-comment"></div>
      <button type="submit" class="submit-btn">送出</button>
    </form>
    <div class="success-toast" id="toast-pro">感謝您的申請！已成功送出。</div>
  </div>
</div>

<!-- ===================== PAGE 6: 聯絡我們 ===================== -->
<div class="page" id="page-contact">
  <div class="contact-box">
    <form id="form-contact" onsubmit="submitForm(event,'contact')">
      <div class="form-row"><label>姓名<span>NAME</span></label><input type="text" id="c-name" required></div>
      <div class="form-row"><label>聯繫電話<span>PHONE</span></label><input type="tel" id="c-phone"></div>
      <div class="form-row"><label>電子信箱<span>EMAIL</span></label><input type="email" id="c-email"></div>
      <div class="form-row"><label>備註<span>COMMENT</span></label><textarea id="c-comment"></textarea></div>
      <button type="submit" class="submit-btn">送出</button>
    </form>
    <div class="success-toast" id="toast-contact">感謝您的來信！已成功送出。</div>
  </div>
</div>

<script>
// ====== GOOGLE SHEETS ENDPOINTS ======
const GS = {
  detail:  'https://script.google.com/macros/s/AKfycbyWstrMfA0Dpwp4pckNQHaa_TpcZG_qcRDJte6j7svUbjB88pEc7ZKPhWriPr6D3UKS/exec',
  share:   'https://script.google.com/macros/s/AKfycbwZsNl9poxWAUekMWFm2Zfkx1Gm6w3SBaAUjf8ybysmz4yEFs8aCCf0jaGWZtgK2r2s/exec',
  pro:     'https://script.google.com/macros/s/AKfycbz-Y1cVIDL4LWkUm9fFg0sS2jPS-8cCzfFqiH7wtoWK5jtf10YFB0T1ai3oJT9C2K-3/exec',
  contact: 'https://script.google.com/macros/s/AKfycbyWstrMfA0Dpwp4pckNQHaa_TpcZG_qcRDJte6j7svUbjB88pEc7ZKPhWriPr6D3UKS/exec'
};

function now() {
  return new Date().toLocaleString('zh-TW', { hour12: false });
}

// ====== PAGE NAV ======
function showPage(id) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('nav a').forEach(a => a.classList.remove('active'));
  const pageMap = { home:'page-home', share:'page-share', contact:'page-contact', pro:'page-pro', results:'page-results', detail:'page-detail' };
  const navMap = { home:'nav-home', share:'nav-share', contact:'nav-contact', pro:'nav-pro' };
  const pg = document.getElementById(pageMap[id]);
  if (pg) pg.classList.add('active');
  const nav = document.getElementById(navMap[id]);
  if (nav) nav.classList.add('active');
  window.scrollTo(0, 0);
}

// ====== SEARCH ======
function toggleOtherDisease(sel) {
  document.getElementById('other-disease-row').style.display = sel.value === '其他' ? 'flex' : 'none';
}

function doSearch() {
  const city = document.getElementById('city-select').value;
  const district = document.getElementById('district-input').value.trim();
  const hospital = document.getElementById('hospital-select').value;
  const disease = document.getElementById('disease-select').value;
  if (!city && !hospital && !disease) {
    alert('請至少選擇一個搜尋條件（縣市、醫院或診斷）');
    return;
  }
  showPage('results');
}

// ====== GEOLOCATION ======
function getLocation() {
  if (!navigator.geolocation) { alert('您的瀏覽器不支援定位功能'); return; }
  navigator.geolocation.getCurrentPosition(
    pos => {
      const { latitude: lat, longitude: lng } = pos.coords;
      const frame = document.getElementById('map-frame');
      frame.innerHTML = `<iframe src="https://maps.google.com/maps?q=${lat},${lng}&z=15&output=embed" allowfullscreen loading="lazy" style="width:100%;height:100%;border:none;"></iframe>`;
      document.getElementById('map-placeholder').style.display = 'none';
      frame.style.display = 'block';
    },
    err => {
      const frame = document.getElementById('map-frame');
      frame.innerHTML = `<iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d115672!2d121.5654!3d25.0330!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3442a9603b0e0e9f%3A0x6db89a12e14c0e14!2sTaipei%2C+Taiwan!5e0!3m2!1szh-TW!2stw!4v1" allowfullscreen loading="lazy" style="width:100%;height:100%;border:none;"></iframe>`;
      document.getElementById('map-placeholder').style.display = 'none';
      frame.style.display = 'block';
      if (err.code === 1) alert('定位權限被拒絕，顯示台灣地圖。');
    }
  );
}

// ====== FORM SUBMIT → GOOGLE SHEETS ======
function submitForm(e, key) {
  e.preventDefault();
  const fields = {
    detail:  { 姓名: 'd-name', 聯繫電話: 'd-phone', 電子信箱: 'd-email', 備注: 'd-comment' },
    share:   { 姓名: 's-name', 聯繫電話: 's-phone', 電子信箱: 's-email', 我要說: 's-comment' },
    pro:     { 團體名稱: 'p-name', 聯繫電話: 'p-phone', 電子信箱: 'p-email', 備註: 'p-comment' },
    contact: { 姓名: 'c-name', 聯繫電話: 'c-phone', 電子信箱: 'c-email', 備註: 'c-comment' },
  };

  const row = { 送出時間: now() };
  Object.entries(fields[key]).forEach(([label, id]) => {
    const el = document.getElementById(id);
    row[label] = el ? el.value : '';
  });

  // Show sending state
  const btn = e.target.querySelector('button[type="submit"]');
  const orig = btn.textContent;
  btn.textContent = '送出中…';
  btn.disabled = true;

  // Send to Google Sheets via no-cors fetch
  fetch(GS[key], {
    method: 'POST',
    mode: 'no-cors',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(row)
  })
  .then(() => {
    const toast = document.getElementById('toast-' + key);
    toast.style.display = 'block';
    setTimeout(() => { toast.style.display = 'none'; }, 4000);
    e.target.reset();
  })
  .catch(() => {
    alert('送出失敗，請檢查網路連線後再試。');
  })
  .finally(() => {
    btn.textContent = orig;
    btn.disabled = false;
  });
}
</script>
</body>
</html>
