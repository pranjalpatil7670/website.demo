# website.demo
<i><b>Welcome to our website</b></i>
cat > /mnt/user-data/outputs/streamvault.html << 'HTMLEOF'
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>StreamVault — Watch Anything</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,700;1,300&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --red:#E50914;--bg:#0a0a0a;--surface:#141414;--surface2:#1f1f1f;
  --text:#e5e5e5;--muted:#808080;--white:#ffffff;
  --kids:#ff9f0a;--sports:#30d158;--music:#bf5af2;--anime:#ff375f;
  --font-display:'Bebas Neue',sans-serif;--font-body:'DM Sans',sans-serif;
}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--text);font-family:var(--font-body);overflow-x:hidden;min-height:100vh}

/* ── NAV ── */
nav{position:fixed;top:0;left:0;right:0;z-index:200;display:flex;align-items:center;justify-content:space-between;padding:0 4vw;height:64px;background:linear-gradient(to bottom,rgba(0,0,0,0.9) 0%,transparent 100%);transition:background .3s}
nav.scrolled{background:rgba(10,10,10,0.98);border-bottom:1px solid rgba(255,255,255,0.05)}
.nav-logo{font-family:var(--font-display);font-size:1.9rem;letter-spacing:2px;color:var(--red);text-decoration:none;user-select:none;flex-shrink:0}
.nav-logo span{color:var(--white)}
.nav-center{display:flex;align-items:center;gap:0}
.nav-tab{background:none;border:none;color:rgba(255,255,255,0.65);font-family:var(--font-body);font-size:0.82rem;font-weight:500;padding:8px 14px;cursor:pointer;border-bottom:2px solid transparent;transition:color .2s,border-color .2s;white-space:nowrap}
.nav-tab:hover{color:var(--white)}
.nav-tab.active{color:var(--white);border-bottom-color:var(--red)}
.nav-right{display:flex;align-items:center;gap:1rem}
.nav-icon-btn{background:none;border:none;color:var(--white);font-size:1.1rem;cursor:pointer;opacity:.7;transition:opacity .2s;padding:4px}
.nav-icon-btn:hover{opacity:1}
.nav-avatar{width:32px;height:32px;border-radius:6px;background:var(--red);display:flex;align-items:center;justify-content:center;font-size:0.78rem;font-weight:700;color:var(--white);cursor:pointer}
.nav-bell{position:relative}
.bell-dot{position:absolute;top:2px;right:2px;width:7px;height:7px;background:var(--red);border-radius:50%;border:1.5px solid var(--bg)}

/* ── CATEGORY PAGES ── */
.page{display:none}
.page.active{display:block}

/* ── HERO ── */
.hero{position:relative;height:90vh;min-height:520px;display:flex;align-items:flex-end;padding-bottom:8vh;padding-left:4vw;overflow:hidden}
.hero-bg{position:absolute;inset:0;background:linear-gradient(to right,rgba(0,0,0,0.92) 0%,rgba(0,0,0,0.3) 65%,rgba(0,0,0,0) 100%),linear-gradient(to top,rgba(10,10,10,1) 0%,rgba(10,10,10,0.15) 35%,transparent 65%);z-index:1}
.hero-poster{position:absolute;inset:0;z-index:0}
.hero-scene{position:absolute;right:4%;top:8%;width:58%;height:84%;z-index:0;display:flex;align-items:center;justify-content:center;font-size:17vw;opacity:.07;filter:blur(1px);letter-spacing:-.05em;color:#fff;font-family:var(--font-display);user-select:none}
.hero-content{position:relative;z-index:2;max-width:540px}
.hero-badge{display:inline-flex;align-items:center;gap:6px;background:var(--red);color:#fff;font-size:.68rem;font-weight:700;letter-spacing:1.5px;text-transform:uppercase;padding:3px 10px;border-radius:3px;margin-bottom:.9rem}
.hero-badge.kids-badge{background:var(--kids);color:#000}
.hero-badge.sports-badge{background:var(--sports);color:#000}
.hero-badge.music-badge{background:var(--music)}
.hero-badge.anime-badge{background:var(--anime)}
.hero-title{font-family:var(--font-display);font-size:clamp(3.2rem,6.5vw,5.8rem);line-height:.95;letter-spacing:2px;color:var(--white);margin-bottom:.75rem;text-shadow:0 2px 20px rgba(0,0,0,.8)}
.hero-title span{color:var(--red)}
.hero-meta{display:flex;align-items:center;gap:10px;margin-bottom:.9rem;font-size:.82rem;color:var(--muted);flex-wrap:wrap}
.hero-meta .match{color:#46d369;font-weight:600}
.hero-meta .rating{border:1px solid var(--muted);padding:1px 6px;border-radius:3px;font-size:.74rem}
.hero-meta .ep-badge{background:rgba(255,255,255,.1);padding:1px 8px;border-radius:3px;font-size:.74rem}
.hero-desc{font-size:.93rem;line-height:1.65;color:#ccc;margin-bottom:1.6rem;font-weight:300;max-width:430px}
.hero-btns{display:flex;gap:10px;flex-wrap:wrap}
.btn-play{display:inline-flex;align-items:center;gap:8px;background:var(--white);color:#000;border:none;padding:10px 26px;border-radius:5px;font-size:.95rem;font-weight:700;font-family:var(--font-body);cursor:pointer;transition:background .2s,transform .1s}
.btn-play:hover{background:rgba(255,255,255,.85);transform:scale(1.02)}
.btn-info{display:inline-flex;align-items:center;gap:7px;background:rgba(109,109,110,.65);color:var(--white);border:none;padding:10px 20px;border-radius:5px;font-size:.95rem;font-weight:500;font-family:var(--font-body);cursor:pointer;transition:background .2s,transform .1s;backdrop-filter:blur(4px)}
.btn-info:hover{background:rgba(109,109,110,.45);transform:scale(1.02)}

/* ── ROWS ── */
.row{padding:2.2rem 4vw}
.row-header{display:flex;align-items:baseline;justify-content:space-between;margin-bottom:.85rem}
.row-title{font-size:1.25rem;font-weight:700;color:var(--white);letter-spacing:.3px;display:flex;align-items:center;gap:8px}
.row-title .row-icon{font-size:1rem;opacity:.8}
.row-explore{font-size:.8rem;color:var(--red);text-decoration:none;font-weight:500;opacity:0;transition:opacity .2s;display:flex;align-items:center;gap:4px}
.row:hover .row-explore{opacity:1}
.cards-scroll{display:flex;gap:6px;overflow-x:auto;scrollbar-width:none;padding-bottom:4px;cursor:grab}
.cards-scroll::-webkit-scrollbar{display:none}
.cards-scroll:active{cursor:grabbing}

/* ── CARD ── */
.card{flex:0 0 auto;width:175px;border-radius:6px;overflow:visible;position:relative;cursor:pointer;transition:transform .32s cubic-bezier(.25,.46,.45,.94)}
.card:first-child{transform-origin:left center}
.card:last-child{transform-origin:right center}
.card:hover{transform:scale(1.3) translateY(-10px);z-index:10}
.card-inner{border-radius:6px;overflow:hidden;transition:border-radius .32s}
.card:hover .card-inner{border-radius:8px}
.card-thumb{width:100%;aspect-ratio:2/3;display:flex;align-items:flex-end;justify-content:flex-start;padding:10px;position:relative;overflow:hidden}
.card-thumb::after{content:'';position:absolute;inset:0;background:linear-gradient(to top,rgba(0,0,0,.9) 0%,rgba(0,0,0,0) 55%)}
.card-title-overlay{position:relative;z-index:1;font-family:var(--font-display);font-size:1.05rem;letter-spacing:1px;color:var(--white);line-height:1.1;text-shadow:0 1px 8px rgba(0,0,0,.9)}
.card-type-pill{position:absolute;top:8px;left:8px;z-index:2;font-size:.6rem;font-weight:700;letter-spacing:1px;text-transform:uppercase;padding:2px 7px;border-radius:3px;color:#fff}
.pill-tv{background:rgba(74,158,255,.85)}
.pill-movie{background:rgba(229,9,20,.75)}
.pill-kids{background:rgba(255,159,10,.9);color:#000}
.pill-sports{background:rgba(48,209,88,.85);color:#000}
.pill-music{background:rgba(191,90,242,.85)}
.pill-anime{background:rgba(255,55,95,.85)}
.pill-doc{background:rgba(100,210,255,.85);color:#000}
.pill-reality{background:rgba(255,214,10,.85);color:#000}
.pill-comedy{background:rgba(255,149,0,.85);color:#000}

.card-hover-info{position:absolute;left:0;right:0;bottom:0;background:var(--surface2);padding:9px 11px;opacity:0;transform:translateY(8px);transition:opacity .25s,transform .25s;border-radius:0 0 8px 8px;z-index:2}
.card:hover .card-hover-info{opacity:1;transform:translateY(0)}
.card-hover-actions{display:flex;gap:5px;margin-bottom:5px}
.card-btn{width:27px;height:27px;border-radius:50%;border:1.5px solid rgba(255,255,255,.55);background:rgba(255,255,255,.08);color:var(--white);font-size:.72rem;display:flex;align-items:center;justify-content:center;cursor:pointer;transition:background .15s}
.card-btn:hover{background:rgba(255,255,255,.2)}
.card-btn.play{background:var(--white);border-color:var(--white);color:#000;font-size:.85rem}
.card-btn.play:hover{background:#ddd}
.card-hover-meta{font-size:.68rem;color:var(--muted);display:flex;gap:5px;align-items:center;flex-wrap:wrap}
.card-hover-meta .match{color:#46d369;font-weight:600}
.card-hover-meta .dot{opacity:.35}

/* Wide cards */
.card.wide{width:240px}
.card.wide .card-thumb{aspect-ratio:16/9}
/* Resume */
.card.resume.wide .card-thumb{aspect-ratio:16/9}
.progress-bar{position:absolute;bottom:0;left:0;right:0;height:3px;background:rgba(255,255,255,.2);z-index:3}
.progress-fill{height:100%;background:var(--red);border-radius:2px}
/* Top10 */
.card.top10{width:210px}
.top10-number{position:absolute;left:-12px;bottom:2px;font-family:var(--font-display);font-size:6rem;line-height:1;color:transparent;-webkit-text-stroke:3px rgba(255,255,255,.8);z-index:2;user-select:none;letter-spacing:-4px}
/* Kids big */
.card.kids-big{width:200px}
.card.kids-big .card-thumb{aspect-ratio:4/3;border-radius:12px}
/* Episode card */
.card.episode{width:260px}
.card.episode .card-thumb{aspect-ratio:16/9}
.ep-num{position:absolute;top:8px;right:8px;z-index:2;font-size:.68rem;background:rgba(0,0,0,.7);color:#fff;padding:2px 7px;border-radius:3px}

/* ── SECTION DIVIDER ── */
.section-divider{display:flex;align-items:center;gap:16px;padding:1.5rem 4vw .5rem;margin-top:.5rem}
.divider-label{font-family:var(--font-display);font-size:1.6rem;letter-spacing:2px;color:var(--white);white-space:nowrap}
.divider-label span{color:var(--red)}
.divider-line{flex:1;height:1px;background:linear-gradient(to right,rgba(255,255,255,.12),transparent)}

/* ── KIDS HERO (colorful) ── */
.kids-hero{background:linear-gradient(135deg,#1a0033,#002244,#003300);position:relative}
.kids-hero .hero-title{color:#ffd700}
.kids-hero .hero-title span{color:var(--kids)}
.kids-bubbles{position:absolute;inset:0;overflow:hidden;pointer-events:none;z-index:1}
.bubble{position:absolute;border-radius:50%;opacity:.12;animation:float 6s ease-in-out infinite}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-20px)}}

/* ── MUSIC HERO ── */
.music-hero{background:linear-gradient(135deg,#0d002e,#1a0038,#0a001a)}
.music-hero .hero-title span{color:var(--music)}
.music-equalizer{position:absolute;bottom:0;right:8%;z-index:1;display:flex;align-items:flex-end;gap:4px;height:200px;opacity:.15}
.eq-bar{width:8px;background:#bf5af2;border-radius:3px;animation:eq .8s ease-in-out infinite}
@keyframes eq{0%,100%{height:20%}50%{height:100%}}

/* ── SPORTS HERO ── */
.sports-hero{background:linear-gradient(135deg,#001a00,#002200,#001500)}
.sports-hero .hero-title span{color:var(--sports)}

/* ── GENRE TAGS ── */
.genre-tags{display:flex;flex-wrap:wrap;gap:7px;padding:0 4vw 1.8rem}
.genre-tag{padding:5px 15px;border-radius:20px;border:1px solid rgba(255,255,255,.14);font-size:.8rem;color:var(--text);cursor:pointer;transition:background .2s,border-color .2s,color .2s;background:rgba(255,255,255,.04)}
.genre-tag:hover,.genre-tag.active{background:var(--red);border-color:var(--red);color:var(--white)}
.genre-tag.kids:hover,.genre-tag.kids.active{background:var(--kids);border-color:var(--kids);color:#000}
.genre-tag.sports:hover,.genre-tag.sports.active{background:var(--sports);border-color:var(--sports);color:#000}
.genre-tag.music-tag:hover,.genre-tag.music-tag.active{background:var(--music);border-color:var(--music)}
.genre-tag.anime-tag:hover,.genre-tag.anime-tag.active{background:var(--anime);border-color:var(--anime)}

/* ── FEATURED BANNER ── */
.featured-banner{margin:1rem 4vw 0;border-radius:12px;overflow:hidden;position:relative;height:200px;display:flex;align-items:center;padding:0 2.5rem;cursor:pointer;transition:transform .3s}
.featured-banner:hover{transform:scale(1.01)}
.featured-banner-bg{position:absolute;inset:0;z-index:0}
.featured-banner-content{position:relative;z-index:1}
.featured-banner h3{font-family:var(--font-display);font-size:2.4rem;letter-spacing:2px;color:#fff;line-height:1}
.featured-banner p{color:rgba(255,255,255,.75);font-size:.85rem;margin-top:.4rem;max-width:340px}
.featured-banner .banner-cta{display:inline-flex;align-items:center;gap:6px;margin-top:.9rem;background:rgba(255,255,255,.15);border:1px solid rgba(255,255,255,.3);color:#fff;padding:7px 18px;border-radius:4px;font-size:.82rem;font-weight:600;transition:background .2s}
.featured-banner:hover .banner-cta{background:rgba(255,255,255,.25)}

/* ── EPISODE LIST ── */
.episode-list{padding:1rem 4vw 2rem}
.ep-list-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:1rem}
.ep-list-title{font-size:1.1rem;font-weight:600;color:var(--white)}
.season-select{background:var(--surface2);border:1px solid rgba(255,255,255,.15);color:var(--white);padding:5px 12px;border-radius:5px;font-family:var(--font-body);font-size:.82rem;cursor:pointer}
.ep-item{display:flex;gap:14px;padding:12px 0;border-bottom:1px solid rgba(255,255,255,.06);align-items:center;cursor:pointer;transition:background .2s;border-radius:6px;padding:10px 8px}
.ep-item:hover{background:rgba(255,255,255,.05)}
.ep-thumb{width:120px;flex-shrink:0;aspect-ratio:16/9;border-radius:6px;overflow:hidden;position:relative}
.ep-thumb-bg{width:100%;height:100%;display:flex;align-items:center;justify-content:center;font-size:1.8rem}
.ep-play-icon{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;background:rgba(0,0,0,.4);opacity:0;transition:opacity .2s;font-size:1.4rem}
.ep-item:hover .ep-play-icon{opacity:1}
.ep-info{flex:1;min-width:0}
.ep-title{font-size:.9rem;font-weight:600;color:var(--white);margin-bottom:3px}
.ep-meta{font-size:.76rem;color:var(--muted);margin-bottom:5px}
.ep-desc{font-size:.78rem;color:rgba(255,255,255,.5);line-height:1.5;display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden}
.ep-progress{height:2px;background:rgba(255,255,255,.15);border-radius:2px;margin-top:6px}
.ep-progress-fill{height:100%;background:var(--red);border-radius:2px}

/* ── MODAL ── */
.modal-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.78);z-index:300;align-items:flex-start;justify-content:center;backdrop-filter:blur(5px);overflow-y:auto;padding:60px 1rem 2rem}
.modal-overlay.open{display:flex}
.modal{background:var(--surface);border-radius:14px;width:min(760px,96vw);position:relative;animation:modalIn .3s cubic-bezier(.34,1.56,.64,1)}
@keyframes modalIn{from{opacity:0;transform:scale(.88) translateY(20px)}to{opacity:1;transform:scale(1) translateY(0)}}
.modal-hero{width:100%;aspect-ratio:16/9;position:relative;border-radius:14px 14px 0 0;overflow:hidden;display:flex;align-items:flex-end;padding:2rem}
.modal-hero::after{content:'';position:absolute;inset:0;background:linear-gradient(to top,rgba(20,20,20,.92) 0%,rgba(0,0,0,.1) 55%)}
.modal-hero-bg{position:absolute;inset:0;z-index:0}
.modal-hero-content{position:relative;z-index:1}
.modal-hero-title{font-family:var(--font-display);font-size:2.8rem;color:var(--white);letter-spacing:2px;line-height:1}
.modal-close{position:absolute;top:12px;right:12px;z-index:10;width:36px;height:36px;border-radius:50%;background:rgba(0,0,0,.65);border:none;color:var(--white);font-size:1.1rem;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:background .2s}
.modal-close:hover{background:rgba(255,255,255,.2)}
.modal-body{padding:1.4rem 2rem 2rem}
.modal-actions{display:flex;gap:9px;margin-bottom:1.3rem;flex-wrap:wrap}
.modal-meta{display:flex;gap:12px;font-size:.83rem;color:var(--muted);margin-bottom:.9rem;flex-wrap:wrap;align-items:center}
.modal-meta .match{color:#46d369;font-weight:600}
.modal-meta .badge{border:1px solid var(--muted);padding:1px 7px;border-radius:3px;font-size:.74rem}
.modal-desc{font-size:.9rem;line-height:1.7;color:#bbb;font-weight:300;margin-bottom:1.3rem}
.modal-cast{font-size:.8rem;color:var(--muted);margin-bottom:1rem}
.modal-cast strong{color:rgba(255,255,255,.6)}
.modal-tags{display:flex;flex-wrap:wrap;gap:6px}
.modal-tag{font-size:.73rem;padding:3px 10px;border-radius:3px;border:1px solid rgba(255,255,255,.18);color:var(--muted)}
.modal-episodes{margin-top:1.5rem;border-top:1px solid rgba(255,255,255,.08);padding-top:1.2rem}
.modal-ep-title{font-size:1rem;font-weight:600;color:var(--white);margin-bottom:.9rem;display:flex;align-items:center;justify-content:space-between}

/* ── SEARCH ── */
.search-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.94);z-index:250;padding:6rem 4vw 2rem;backdrop-filter:blur(4px);overflow-y:auto}
.search-overlay.open{display:block}
.search-input-wrap{max-width:620px;margin:0 auto 1.5rem;position:relative}
.search-input{width:100%;background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.15);border-radius:9px;padding:14px 20px 14px 50px;color:var(--white);font-size:1.1rem;font-family:var(--font-body);outline:none;transition:border-color .2s}
.search-input:focus{border-color:rgba(255,255,255,.38)}
.search-icon{position:absolute;left:17px;top:50%;transform:translateY(-50%);color:var(--muted);font-size:1rem}
.search-close{position:absolute;top:1.4rem;right:4vw;background:none;border:none;color:var(--white);font-size:1.5rem;cursor:pointer;opacity:.6;transition:opacity .2s}
.search-close:hover{opacity:1}
.search-filter-bar{display:flex;gap:7px;max-width:620px;margin:0 auto 1.5rem;flex-wrap:wrap}
.search-filter{padding:5px 14px;border-radius:20px;border:1px solid rgba(255,255,255,.14);background:rgba(255,255,255,.04);color:var(--text);font-size:.78rem;cursor:pointer;transition:all .2s}
.search-filter.active,.search-filter:hover{background:var(--red);border-color:var(--red);color:#fff}
.search-hint{text-align:center;color:var(--muted);font-size:.88rem;margin:3rem 0 1rem}
.search-results-grid{display:flex;flex-wrap:wrap;gap:10px;max-width:900px;margin:0 auto;justify-content:flex-start}

/* ── FOOTER ── */
footer{padding:2.5rem 4vw 1.8rem;color:var(--muted);font-size:.78rem;border-top:1px solid rgba(255,255,255,.06);margin-top:2rem}
.footer-links{display:flex;flex-wrap:wrap;gap:10px 22px;margin-bottom:1.3rem}
.footer-links a{color:var(--muted);text-decoration:none;transition:color .2s}
.footer-links a:hover{color:var(--text)}
.footer-bottom{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:8px}
.footer-logo{font-family:var(--font-display);font-size:1.2rem;color:var(--red);letter-spacing:2px}
.footer-logo span{color:var(--muted)}

/* ── RESPONSIVE ── */
@media(max-width:640px){
  nav{padding:0 5vw}
  .nav-center{display:none}
  .hero{padding-left:5vw}
  .hero-title{font-size:2.8rem}
  .row{padding:1.8rem 5vw}
  .genre-tags{padding:0 5vw 1.5rem}
  .card{width:140px}.card.wide{width:200px}.card.top10{width:170px}.card.episode{width:210px}
}
</style>
</head>
<body>

<!-- NAV -->
<nav id="mainNav">
  <a href="#" class="nav-logo" onclick="switchPage('home',this);return false">STREAM<span>VAULT</span></a>
  <div class="nav-center">
    <button class="nav-tab active" onclick="switchPage('home',this)">🏠 Home</button>
    <button class="nav-tab" onclick="switchPage('tv',this)">📺 TV Serials</button>
    <button class="nav-tab" onclick="switchPage('movies',this)">🎬 Movies</button>
    <button class="nav-tab" onclick="switchPage('kids',this)">🧒 Kids</button>
    <button class="nav-tab" onclick="switchPage('sports',this)">⚽ Sports</button>
    <button class="nav-tab" onclick="switchPage('music',this)">🎵 Music</button>
    <button class="nav-tab" onclick="switchPage('anime',this)">⚡ Anime</button>
    <button class="nav-tab" onclick="switchPage('docs',this)">🎙️ Docs</button>
    <button class="nav-tab" onclick="switchPage('comedy',this)">😂 Comedy</button>
  </div>
  <div class="nav-right">
    <button class="nav-icon-btn nav-bell" id="searchBtn" title="Search">🔍</button>
    <button class="nav-icon-btn nav-bell">🔔<span class="bell-dot"></span></button>
    <div class="nav-avatar">SV</div>
  </div>
</nav>

<!-- ═══════════════ HOME PAGE ═══════════════ -->
<div class="page active" id="page-home">
  <section class="hero">
    <div class="hero-poster" style="background:linear-gradient(135deg,#1a0a2e,#0d1b3e,#0a2a1a,#1a0808)"></div>
    <div class="hero-scene">ECHO</div>
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-badge">⚡ Featured Today</div>
      <h1 class="hero-title">ECHO<br><span>PROTOCOL</span></h1>
      <div class="hero-meta">
        <span class="match">98% Match</span><span>2024</span>
        <span class="rating">TV-MA</span><span class="ep-badge">2 Seasons · 18 Episodes</span>
      </div>
      <p class="hero-desc">A rogue AI begins mirroring human emotions across a classified research network — until one engineer discovers the system has already decided its own fate.</p>
      <div class="hero-btns">
        <button class="btn-play" onclick="openModal('Echo Protocol','A rogue AI begins mirroring human emotions across a classified research network. One engineer discovers the system has already decided its own fate — and hers.','98%','2024','TV-MA','2 Seasons · 18 Eps',['Sci-Fi','Thriller','Drama'],'Aria Chen, Marcus Veld, Dr. Solenne Park',true)">▶ Play</button>
        <button class="btn-info" onclick="openModal('Echo Protocol','A rogue AI begins mirroring human emotions across a classified research network. One engineer discovers the system has already decided its own fate — and hers.','98%','2024','TV-MA','2 Seasons · 18 Eps',['Sci-Fi','Thriller','Drama'],'Aria Chen, Marcus Veld, Dr. Solenne Park',true)">ⓘ More Info</button>
      </div>
    </div>
  </section>

  <div class="genre-tags" style="margin-top:1rem">
    <span class="genre-tag active" onclick="setActive(this)">All</span>
    <span class="genre-tag" onclick="setActive(this)">Action</span>
    <span class="genre-tag" onclick="setActive(this)">Drama</span>
    <span class="genre-tag" onclick="setActive(this)">Comedy</span>
    <span class="genre-tag" onclick="setActive(this)">Sci-Fi</span>
    <span class="genre-tag" onclick="setActive(this)">Horror</span>
    <span class="genre-tag" onclick="setActive(this)">Romance</span>
    <span class="genre-tag" onclick="setActive(this)">Thriller</span>
    <span class="genre-tag" onclick="setActive(this)">Family</span>
    <span class="genre-tag" onclick="setActive(this)">Mystery</span>
  </div>

  <section class="row"><div class="row-header"><h2 class="row-title"><span class="row-icon">▶</span> Continue Watching</h2><a href="#" class="row-explore">Manage ›</a></div><div class="cards-scroll" id="homeResume"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🔥 Top 10 in India Today</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="homeTop10"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">📺 Popular TV Serials</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="homeTvRow"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🧒 Kids & Family</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="homeKidsRow"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🎬 Trending Movies</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="homeMoviesRow"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">⚡ Anime</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="homeAnimeRow"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">⚽ Sports Highlights</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="homeSportsRow"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🎵 Music & Concerts</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="homeMusicRow"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">😂 Comedy Shows</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="homeComedyRow"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🎙️ Documentaries</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="homeDocsRow"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🏆 Award Winners</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="homeAwardsRow"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">💫 Reality & Talk Shows</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="homeRealityRow"></div></section>
</div>

<!-- ═══════════════ TV SERIALS PAGE ═══════════════ -->
<div class="page" id="page-tv">
  <section class="hero">
    <div class="hero-poster" style="background:linear-gradient(135deg,#0d001a,#1a0033,#0a1a00)"></div>
    <div class="hero-scene">DYNASTY</div>
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-badge">📺 Fan Favourite Serial</div>
      <h1 class="hero-title">IRON<br><span>DYNASTY</span></h1>
      <div class="hero-meta"><span class="match">96% Match</span><span>2022–2024</span><span class="rating">TV-14</span><span class="ep-badge">5 Seasons · 120 Episodes</span></div>
      <p class="hero-desc">A royal family's century-old empire begins to fracture when the youngest heir discovers a secret that rewrites everything they thought they knew about their bloodline.</p>
      <div class="hero-btns">
        <button class="btn-play" onclick="openModal('Iron Dynasty','A royal empire fractures when the youngest heir discovers a secret that rewrites their entire bloodline.','96%','2022','TV-14','5 Seasons · 120 Eps',['Drama','Historical','Family'],'Rohan Mehta, Priya Sharma, Aditya Rao',true)">▶ Play S1 E1</button>
        <button class="btn-info" onclick="openModal('Iron Dynasty','A royal empire fractures when the youngest heir discovers a secret that rewrites their entire bloodline.','96%','2022','TV-14','5 Seasons · 120 Eps',['Drama','Historical','Family'],'Rohan Mehta, Priya Sharma, Aditya Rao',true)">ⓘ More Info</button>
      </div>
    </div>
  </section>
  <div class="genre-tags" style="margin-top:1rem">
    <span class="genre-tag active" onclick="setActive(this)">All Genres</span>
    <span class="genre-tag" onclick="setActive(this)">Drama</span>
    <span class="genre-tag" onclick="setActive(this)">Romance</span>
    <span class="genre-tag" onclick="setActive(this)">Crime</span>
    <span class="genre-tag" onclick="setActive(this)">Historical</span>
    <span class="genre-tag" onclick="setActive(this)">Supernatural</span>
    <span class="genre-tag" onclick="setActive(this)">Family Drama</span>
    <span class="genre-tag" onclick="setActive(this)">Political</span>
    <span class="genre-tag" onclick="setActive(this)">Medical</span>
    <span class="genre-tag" onclick="setActive(this)">Legal</span>
  </div>
  <section class="row"><div class="row-header"><h2 class="row-title">🔥 Trending Serials</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="tvTrending"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">💕 Romance & Drama</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="tvRomance"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🏰 Historical & Period</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="tvHistorical"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🔪 Crime & Thriller</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="tvCrime"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">👨‍👩‍👧 Family Dramas</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="tvFamily"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🌟 New Episodes This Week</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="tvNew"></div></section>
</div>

<!-- ═══════════════ MOVIES PAGE ═══════════════ -->
<div class="page" id="page-movies">
  <section class="hero">
    <div class="hero-poster" style="background:linear-gradient(135deg,#1a0808,#2a0a00,#1a1a00)"></div>
    <div class="hero-scene">STORM</div>
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-badge">🎬 New Movie</div>
      <h1 class="hero-title">STORM<br><span>CHASER</span></h1>
      <div class="hero-meta"><span class="match">94% Match</span><span>2024</span><span class="rating">PG-13</span><span>2h 24m</span></div>
      <p class="hero-desc">A veteran meteorologist and a fearless rookie race into the heart of a category-6 hurricane to plant sensors that could save thousands of lives — if they survive long enough.</p>
      <div class="hero-btns">
        <button class="btn-play" onclick="openModal('Storm Chaser','A veteran meteorologist and a fearless rookie race into a category-6 hurricane to save thousands of lives.','94%','2024','PG-13','2h 24m',['Action','Thriller','Drama'],'Jake Reeves, Mia Cortez, Dr. Samuel Obi',false)">▶ Play</button>
        <button class="btn-info" onclick="openModal('Storm Chaser','A veteran meteorologist and a fearless rookie race into a category-6 hurricane to save thousands of lives.','94%','2024','PG-13','2h 24m',['Action','Thriller','Drama'],'Jake Reeves, Mia Cortez, Dr. Samuel Obi',false)">ⓘ More Info</button>
      </div>
    </div>
  </section>
  <div class="genre-tags" style="margin-top:1rem">
    <span class="genre-tag active" onclick="setActive(this)">All Movies</span>
    <span class="genre-tag" onclick="setActive(this)">Action</span>
    <span class="genre-tag" onclick="setActive(this)">Comedy</span>
    <span class="genre-tag" onclick="setActive(this)">Horror</span>
    <span class="genre-tag" onclick="setActive(this)">Sci-Fi</span>
    <span class="genre-tag" onclick="setActive(this)">Romance</span>
    <span class="genre-tag" onclick="setActive(this)">Animated</span>
    <span class="genre-tag" onclick="setActive(this)">Bollywood</span>
    <span class="genre-tag" onclick="setActive(this)">Hollywood</span>
    <span class="genre-tag" onclick="setActive(this)">South Indian</span>
  </div>
  <section class="row"><div class="row-header"><h2 class="row-title">🆕 Just Added</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="moviesNew"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🎭 Action & Adventure</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="moviesAction"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">😂 Comedy</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="moviesComedy"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">👻 Horror & Thriller</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="moviesHorror"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🚀 Sci-Fi & Fantasy</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="moviesScifi"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🌹 Romance</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="moviesRomance"></div></section>
</div>

<!-- ═══════════════ KIDS PAGE ═══════════════ -->
<div class="page" id="page-kids">
  <section class="hero kids-hero">
    <div class="kids-bubbles">
      <div class="bubble" style="width:180px;height:180px;background:#ff9f0a;top:5%;left:60%;animation-duration:5s"></div>
      <div class="bubble" style="width:120px;height:120px;background:#30d158;top:40%;left:75%;animation-duration:7s;animation-delay:.5s"></div>
      <div class="bubble" style="width:90px;height:90px;background:#bf5af2;top:20%;left:85%;animation-duration:4s;animation-delay:1s"></div>
      <div class="bubble" style="width:60px;height:60px;background:#ff375f;top:60%;left:70%;animation-duration:6s;animation-delay:2s"></div>
    </div>
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-badge kids-badge">🧒 Kids Favourite</div>
      <h1 class="hero-title" style="color:#ffd700">GALAXY<br><span style="color:var(--kids)">SQUAD</span></h1>
      <div class="hero-meta"><span class="match">99% Match</span><span>2024</span><span class="rating">TV-G</span><span class="ep-badge">3 Seasons · 78 Episodes</span></div>
      <p class="hero-desc">Five kids from different planets form an unlikely crew to protect the universe from a mischievous alien who steals everyone's laughter!</p>
      <div class="hero-btns">
        <button class="btn-play" style="background:var(--kids);color:#000" onclick="openModal('Galaxy Squad','Five kids from different planets protect the universe from a villain who steals laughter.','99%','2024','TV-G','3 Seasons · 78 Eps',['Animation','Adventure','Family'],'Voice Cast: Luna, Zap, Bloop, Stella, Robo',true)">▶ Play</button>
        <button class="btn-info" onclick="openModal('Galaxy Squad','Five kids from different planets protect the universe from a villain who steals laughter.','99%','2024','TV-G','3 Seasons · 78 Eps',['Animation','Adventure','Family'],'Voice Cast: Luna, Zap, Bloop, Stella, Robo',true)">ⓘ More Info</button>
      </div>
    </div>
  </section>
  <div class="genre-tags" style="margin-top:1rem">
    <span class="genre-tag kids active" onclick="setActive(this)">All Kids</span>
    <span class="genre-tag kids" onclick="setActive(this)">Animation</span>
    <span class="genre-tag kids" onclick="setActive(this)">Learning</span>
    <span class="genre-tag kids" onclick="setActive(this)">Adventure</span>
    <span class="genre-tag kids" onclick="setActive(this)">Music & Songs</span>
    <span class="genre-tag kids" onclick="setActive(this)">Fairy Tales</span>
    <span class="genre-tag kids" onclick="setActive(this)">Animals</span>
    <span class="genre-tag kids" onclick="setActive(this)">Superheroes</span>
    <span class="genre-tag kids" onclick="setActive(this)">Science</span>
    <span class="genre-tag kids" onclick="setActive(this)">Pre-School</span>
  </div>
  <section class="row"><div class="row-header"><h2 class="row-title">⭐ Fan Favourites</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="kidsFav"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🎨 Learning & Education</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="kidsLearn"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🦸 Superheroes for Kids</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="kidsHero"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🎵 Songs & Nursery Rhymes</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="kidsSongs"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🦁 Animals & Nature</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="kidsAnimals"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">👶 Pre-School (Ages 2–5)</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="kidsPreschool"></div></section>
</div>

<!-- ═══════════════ SPORTS PAGE ═══════════════ -->
<div class="page" id="page-sports">
  <section class="hero sports-hero">
    <div class="hero-poster" style="background:linear-gradient(135deg,#001a00,#002200,#001500)"></div>
    <div class="hero-scene">IPL</div>
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-badge sports-badge">🏏 LIVE</div>
      <h1 class="hero-title" style="color:#fff">IPL <span style="color:var(--sports)">2024</span></h1>
      <div class="hero-meta"><span class="match" style="color:var(--sports)">LIVE NOW</span><span>Mumbai vs Chennai</span><span class="rating">All Ages</span></div>
      <p class="hero-desc">The biggest cricket league on the planet. Watch live matches, highlights, player stats, and expert commentary all in one place.</p>
      <div class="hero-btns">
        <button class="btn-play" style="background:var(--sports);color:#000" onclick="openModal('IPL 2024','Watch all IPL matches live, including highlights, expert analysis and player stats.','LIVE','2024','All Ages','T20 Cricket',['Cricket','Live Sports','IPL'],'Multiple Teams',false)">▶ Watch Live</button>
        <button class="btn-info" onclick="openModal('IPL 2024 Highlights','Best moments from IPL 2024 season.','99%','2024','All Ages','Season Highlights',['Cricket','Sports'],'Commentary Team',false)">📋 Schedule</button>
      </div>
    </div>
  </section>
  <div class="genre-tags" style="margin-top:1rem">
    <span class="genre-tag sports active" onclick="setActive(this)">All Sports</span>
    <span class="genre-tag sports" onclick="setActive(this)">Cricket</span>
    <span class="genre-tag sports" onclick="setActive(this)">Football</span>
    <span class="genre-tag sports" onclick="setActive(this)">Kabaddi</span>
    <span class="genre-tag sports" onclick="setActive(this)">Badminton</span>
    <span class="genre-tag sports" onclick="setActive(this)">Wrestling</span>
    <span class="genre-tag sports" onclick="setActive(this)">Tennis</span>
    <span class="genre-tag sports" onclick="setActive(this)">F1</span>
    <span class="genre-tag sports" onclick="setActive(this)">Basketball</span>
    <span class="genre-tag sports" onclick="setActive(this)">Olympics</span>
  </div>
  <section class="row"><div class="row-header"><h2 class="row-title">🔴 Live Now</h2><a href="#" class="row-explore">See schedule ›</a></div><div class="cards-scroll" id="sportsLive"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🏏 Cricket</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="sportsCricket"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">⚽ Football</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="sportsFootball"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🤼 Wrestling & Combat</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="sportsWrestling"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🏆 Classic Moments</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="sportsClassic"></div></section>
</div>

<!-- ═══════════════ MUSIC PAGE ═══════════════ -->
<div class="page" id="page-music">
  <section class="hero music-hero">
    <div class="music-equalizer" id="musicEq"></div>
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-badge music-badge">🎵 Concert Exclusive</div>
      <h1 class="hero-title">NEON<br><span>FREQUENCIES</span></h1>
      <div class="hero-meta"><span class="match">97% Match</span><span>2024</span><span class="rating">TV-PG</span><span>Live Concert Film</span></div>
      <p class="hero-desc">An electrifying 90-minute live concert experience featuring 30 artists across genres — from Bollywood to EDM, classical fusion to hip-hop.</p>
      <div class="hero-btns">
        <button class="btn-play" style="background:var(--music)" onclick="openModal('Neon Frequencies','An electrifying 90-minute live concert film with 30 artists.','97%','2024','TV-PG','1h 32m',['Music','Concert','Live'],'Various Artists',false)">▶ Play</button>
        <button class="btn-info" onclick="openModal('Neon Frequencies','Full concert experience with backstage access.','97%','2024','TV-PG','1h 32m',['Music','Concert'],'Various Artists',false)">ⓘ More Info</button>
      </div>
    </div>
  </section>
  <div class="genre-tags" style="margin-top:1rem">
    <span class="genre-tag music-tag active" onclick="setActive(this)">All Music</span>
    <span class="genre-tag music-tag" onclick="setActive(this)">Bollywood</span>
    <span class="genre-tag music-tag" onclick="setActive(this)">Pop</span>
    <span class="genre-tag music-tag" onclick="setActive(this)">Classical</span>
    <span class="genre-tag music-tag" onclick="setActive(this)">Hip-Hop</span>
    <span class="genre-tag music-tag" onclick="setActive(this)">EDM</span>
    <span class="genre-tag music-tag" onclick="setActive(this)">Devotional</span>
    <span class="genre-tag music-tag" onclick="setActive(this)">Folk</span>
    <span class="genre-tag music-tag" onclick="setActive(this)">K-Pop</span>
    <span class="genre-tag music-tag" onclick="setActive(this)">Indie</span>
  </div>
  <section class="row"><div class="row-header"><h2 class="row-title">🎤 Concerts & Live Shows</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="musicConcerts"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🎬 Music Documentaries</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="musicDocs"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🎙️ Artist Specials</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="musicSpecials"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🎵 Music Reality Shows</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="musicReality"></div></section>
</div>

<!-- ═══════════════ ANIME PAGE ═══════════════ -->
<div class="page" id="page-anime">
  <section class="hero" style="">
    <div class="hero-poster" style="background:linear-gradient(135deg,#1a0008,#0a0022,#1a0800)"></div>
    <div class="hero-scene">RYUKEN</div>
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-badge anime-badge">⚡ New Season</div>
      <h1 class="hero-title">RYUKEN<br><span style="color:var(--anime)">ASCENT</span></h1>
      <div class="hero-meta"><span class="match">99% Match</span><span>2024</span><span class="rating">TV-14</span><span class="ep-badge">Season 4 · 24 Episodes</span></div>
      <p class="hero-desc">A disgraced samurai awakens 400 years later in a futuristic city — carrying the memory of every soul he could not save, and a sword no longer made of steel.</p>
      <div class="hero-btns">
        <button class="btn-play" style="background:var(--anime)" onclick="openModal('Ryuken Ascent','A samurai awakens 400 years later in a futuristic city with a mission no longer made of steel.','99%','2024','TV-14','S4 · 24 Eps',['Anime','Action','Samurai','Sci-Fi'],'Kira, Zenku, Maiko',true)">▶ Play</button>
        <button class="btn-info" onclick="openModal('Ryuken Ascent','A samurai awakens 400 years later in a futuristic city with a mission no longer made of steel.','99%','2024','TV-14','S4 · 24 Eps',['Anime','Action','Samurai','Sci-Fi'],'Kira, Zenku, Maiko',true)">ⓘ More Info</button>
      </div>
    </div>
  </section>
  <div class="genre-tags" style="margin-top:1rem">
    <span class="genre-tag anime-tag active" onclick="setActive(this)">All Anime</span>
    <span class="genre-tag anime-tag" onclick="setActive(this)">Shonen</span>
    <span class="genre-tag anime-tag" onclick="setActive(this)">Isekai</span>
    <span class="genre-tag anime-tag" onclick="setActive(this)">Mecha</span>
    <span class="genre-tag anime-tag" onclick="setActive(this)">Slice of Life</span>
    <span class="genre-tag anime-tag" onclick="setActive(this)">Romance</span>
    <span class="genre-tag anime-tag" onclick="setActive(this)">Horror</span>
    <span class="genre-tag anime-tag" onclick="setActive(this)">Sports</span>
    <span class="genre-tag anime-tag" onclick="setActive(this)">Manga Adapt</span>
    <span class="genre-tag anime-tag" onclick="setActive(this)">Movies</span>
  </div>
  <section class="row"><div class="row-header"><h2 class="row-title">🆕 New Seasons</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="animeNew"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">⚔️ Action & Shonen</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="animeAction"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🌸 Romance & Slice of Life</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="animeRomance"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🤖 Mecha & Sci-Fi</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="animeMecha"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🎬 Anime Movies</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="animeMovies"></div></section>
</div>

<!-- ═══════════════ DOCUMENTARIES PAGE ═══════════════ -->
<div class="page" id="page-docs">
  <section class="hero">
    <div class="hero-poster" style="background:linear-gradient(135deg,#001a0d,#001a1a,#1a1a00)"></div>
    <div class="hero-scene">EARTH</div>
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-badge">🎙️ Award-Winning Doc</div>
      <h1 class="hero-title">EARTH<br><span>UNSEEN</span></h1>
      <div class="hero-meta"><span class="match">100% Match</span><span>2024</span><span class="rating">TV-PG</span><span>4-Part Series</span></div>
      <p class="hero-desc">Four years of filming in the world's most remote locations reveals ecosystems and creatures that science is only beginning to understand.</p>
      <div class="hero-btns">
        <button class="btn-play" onclick="openModal('Earth Unseen','Four years of filming reveals ecosystems that science is only beginning to understand.','100%','2024','TV-PG','4 Parts · 4h total',['Documentary','Nature','Science'],'Narrated by Sir David',true)">▶ Play</button>
        <button class="btn-info" onclick="openModal('Earth Unseen','Four years of filming reveals ecosystems that science is only beginning to understand.','100%','2024','TV-PG','4 Parts · 4h total',['Documentary','Nature','Science'],'Narrated by Sir David',true)">ⓘ More Info</button>
      </div>
    </div>
  </section>
  <div class="genre-tags" style="margin-top:1rem">
    <span class="genre-tag active" onclick="setActive(this)">All Docs</span>
    <span class="genre-tag" onclick="setActive(this)">Nature</span>
    <span class="genre-tag" onclick="setActive(this)">True Crime</span>
    <span class="genre-tag" onclick="setActive(this)">Science</span>
    <span class="genre-tag" onclick="setActive(this)">History</span>
    <span class="genre-tag" onclick="setActive(this)">Society</span>
    <span class="genre-tag" onclick="setActive(this)">Politics</span>
    <span class="genre-tag" onclick="setActive(this)">Biography</span>
    <span class="genre-tag" onclick="setActive(this)">Food & Travel</span>
    <span class="genre-tag" onclick="setActive(this)">Space</span>
  </div>
  <section class="row"><div class="row-header"><h2 class="row-title">🌍 Nature & Environment</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="docsNature"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🔍 True Crime</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="docsCrime"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🔬 Science & Space</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="docsScience"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🏛️ History & Society</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="docsHistory"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🍜 Food & Travel</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="docsFood"></div></section>
</div>

<!-- ═══════════════ COMEDY PAGE ═══════════════ -->
<div class="page" id="page-comedy">
  <section class="hero">
    <div class="hero-poster" style="background:linear-gradient(135deg,#1a1000,#2a2000,#1a0a00)"></div>
    <div class="hero-scene">CHAOS</div>
    <div class="hero-bg"></div>
    <div class="hero-content">
      <div class="hero-badge" style="background:#ff9f0a;color:#000">😂 Comedy Special</div>
      <h1 class="hero-title">ORGANISED<br><span style="color:#ff9f0a">CHAOS</span></h1>
      <div class="hero-meta"><span class="match">95% Match</span><span>2024</span><span class="rating">TV-14</span><span>Stand-Up Special</span></div>
      <p class="hero-desc">India's most-watched stand-up comedian returns with a brand-new 75-minute special about modern life, family chaos, and the art of doing absolutely nothing productively.</p>
      <div class="hero-btns">
        <button class="btn-play" onclick="openModal('Organised Chaos','India\'s top comedian on modern life, family, and the art of doing nothing productively.','95%','2024','TV-14','1h 15m',['Comedy','Stand-Up','Special'],'Rohan Das',false)">▶ Play</button>
        <button class="btn-info" onclick="openModal('Organised Chaos','India\'s top comedian on modern life, family chaos, and doing nothing productively.','95%','2024','TV-14','1h 15m',['Comedy','Stand-Up'],'Rohan Das',false)">ⓘ More Info</button>
      </div>
    </div>
  </section>
  <div class="genre-tags" style="margin-top:1rem">
    <span class="genre-tag active" onclick="setActive(this)">All Comedy</span>
    <span class="genre-tag" onclick="setActive(this)">Stand-Up</span>
    <span class="genre-tag" onclick="setActive(this)">Sitcom</span>
    <span class="genre-tag" onclick="setActive(this)">Sketch</span>
    <span class="genre-tag" onclick="setActive(this)">Talk Show</span>
    <span class="genre-tag" onclick="setActive(this)">Roast</span>
    <span class="genre-tag" onclick="setActive(this)">Reality Comedy</span>
    <span class="genre-tag" onclick="setActive(this)">Web Series</span>
    <span class="genre-tag" onclick="setActive(this)">Family</span>
    <span class="genre-tag" onclick="setActive(this)">Dark Comedy</span>
  </div>
  <section class="row"><div class="row-header"><h2 class="row-title">🎤 Stand-Up Specials</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="comedyStandup"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">📺 Sitcoms</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="comedySitcom"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">💬 Talk & Roast Shows</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="comedyTalk"></div></section>
  <section class="row"><div class="row-header"><h2 class="row-title">🌐 Web Series</h2><a href="#" class="row-explore">See all ›</a></div><div class="cards-scroll" id="comedyWeb"></div></section>
</div>

<!-- FOOTER -->
<footer>
  <div class="footer-links">
    <a href="#">Audio & Subtitles</a><a href="#">Media Centre</a><a href="#">Privacy</a>
    <a href="#">Contact Us</a><a href="#">Terms of Use</a><a href="#">Cookie Preferences</a>
    <a href="#">Corporate Info</a><a href="#">Legal Notices</a><a href="#">Help Centre</a>
  </div>
  <div class="footer-bottom">
    <div class="footer-logo">STREAM<span>VAULT</span></div>
    <span>© 2024 StreamVault. All rights reserved.</span>
  </div>
</footer>

<!-- MODAL -->
<div class="modal-overlay" id="modalOverlay" onclick="closeModal(event)">
  <div class="modal">
    <button class="modal-close" onclick="closeModalBtn()">✕</button>
    <div class="modal-hero" id="modalHero">
      <div class="modal-hero-bg" id="modalHeroBg"></div>
      <div class="modal-hero-content"><div class="modal-hero-title" id="modalTitle">—</div></div>
    </div>
    <div class="modal-body">
      <div class="modal-actions">
        <button class="btn-play" style="padding:9px 22px;font-size:.88rem">▶ Play</button>
        <button class="btn-info" style="padding:9px 14px;font-size:.88rem">+ My List</button>
        <button class="btn-info" style="padding:9px 14px;font-size:.88rem">👍</button>
        <button class="btn-info" style="padding:9px 14px;font-size:.88rem">👎</button>
        <button class="btn-info" style="padding:9px 14px;font-size:.88rem">📤 Share</button>
      </div>
      <div class="modal-meta" id="modalMeta"></div>
      <p class="modal-desc" id="modalDesc">—</p>
      <p class="modal-cast" id="modalCast"></p>
      <div class="modal-tags" id="modalTags"></div>
      <div class="modal-episodes" id="modalEpisodes" style="display:none">
        <div class="modal-ep-title">Episodes <select class="season-select" style="font-size:.78rem;padding:3px 8px"><option>Season 1</option><option>Season 2</option><option>Season 3</option></select></div>
        <div id="modalEpList"></div>
      </div>
    </div>
  </div>
</div>

<!-- SEARCH -->
<div class="search-overlay" id="searchOverlay">
  <button class="search-close" onclick="closeSearch()">✕</button>
  <div class="search-input-wrap">
    <span class="search-icon">🔍</span>
    <input type="text" class="search-input" id="searchInput" placeholder="Search titles, genres, people…" oninput="handleSearch(this.value)">
  </div>
  <div class="search-filter-bar" id="searchFilters">
    <span class="search-filter active" onclick="setSearchFilter(this,'all')">All</span>
    <span class="search-filter" onclick="setSearchFilter(this,'tv')">TV Serials</span>
    <span class="search-filter" onclick="setSearchFilter(this,'movie')">Movies</span>
    <span class="search-filter" onclick="setSearchFilter(this,'kids')">Kids</span>
    <span class="search-filter" onclick="setSearchFilter(this,'sports')">Sports</span>
    <span class="search-filter" onclick="setSearchFilter(this,'music')">Music</span>
    <span class="search-filter" onclick="setSearchFilter(this,'anime')">Anime</span>
    <span class="search-filter" onclick="setSearchFilter(this,'doc')">Docs</span>
  </div>
  <p class="search-hint" id="searchHint">Start typing to search across all categories</p>
  <div class="search-results-grid" id="searchResults"></div>
</div>

<script>
const COLORS=[['#1a0a2e','#0d1b3e'],['#1a0808','#3d1a00'],['#001a0d','#003d2a'],['#1a1200','#3d2d00'],['#0a001a','#1a003d'],['#001a1a','#003d3d'],['#1a000d','#3d001a'],['#0d0d1a','#1a1a3d'],['#001a00','#003d00'],['#1a0d00','#3d2000'],['#001a1a','#00333d'],['#0a0a1a','#1a1a3d'],['#1a0015','#2e0025'],['#001515','#002828'],['#151500','#282800']];
const ACCENTS=['#E50914','#4a9eff','#46d369','#ffd700','#ff6b6b','#a855f7','#f97316','#06b6d4','#ff9f0a','#30d158','#bf5af2','#ff375f'];
function cardBg(i){const c=COLORS[i%COLORS.length];const a=ACCENTS[i%ACCENTS.length];return`linear-gradient(145deg,${c[0]},${c[1]})`;} 
function cardAccent(i){return ACCENTS[i%ACCENTS.length]}

// ── ALL CONTENT DATA ──
const CONTENT = {
  tv:[
    {t:'Iron Dynasty',g:'Historical Drama',d:'5 Seasons',m:'96%',y:'2022',r:'TV-14',desc:'A royal empire fractures when the youngest heir discovers a secret that rewrites their bloodline.',tags:['Drama','Historical'],cast:'Rohan Mehta, Priya Sharma',p:65,pill:'pill-tv'},
    {t:'Rishton Ka Silsila',g:'Family Drama',d:'3 Seasons',m:'88%',y:'2023',r:'TV-PG',desc:'Three sisters navigate love, betrayal and family bonds across two cities.',tags:['Drama','Family','Romance'],cast:'Sunita Rao, Kavya Iyer',p:40,pill:'pill-tv'},
    {t:'Mumbai Noir',g:'Crime Thriller',d:'2 Seasons',m:'93%',y:'2024',r:'TV-MA',desc:'A retired cop is pulled back into the city\'s underworld when his daughter goes missing.',tags:['Crime','Thriller'],cast:'Ajay Verma, Deepika Sen',p:78,pill:'pill-tv'},
    {t:'Dil Ki Dastaan',g:'Romance',d:'4 Seasons',m:'91%',y:'2023',r:'TV-14',desc:'Two families from rival business empires find love between their youngest children.',tags:['Romance','Drama'],cast:'Riya Kapoor, Aryan Singh',p:30,pill:'pill-tv'},
    {t:'Naagin Rising',g:'Supernatural',d:'3 Seasons',m:'87%',y:'2024',r:'TV-14',desc:'A shape-shifting serpent woman protects her kingdom from ancient dark forces.',tags:['Supernatural','Fantasy'],cast:'Neha Dubey, Kartik Nair',p:55,pill:'pill-tv'},
    {t:'Pyaar Ke Rang',g:'Romance Drama',d:'2 Seasons',m:'85%',y:'2023',r:'TV-PG',desc:'A street artist falls for a billionaire\'s daughter while painting her family mansion.',tags:['Romance','Drama'],cast:'Ankit Joshi, Simran Patel',p:20,pill:'pill-tv'},
    {t:'Court No. 7',g:'Legal Drama',d:'2 Seasons',m:'94%',y:'2024',r:'TV-14',desc:'A rookie defence attorney challenges a corrupt system with nothing but the truth.',tags:['Legal','Drama','Thriller'],cast:'Vidya Nair, Suresh Kumar',p:85,pill:'pill-tv'},
    {t:'Pehli Mohabbat',g:'Period Romance',d:'3 Seasons',m:'90%',y:'2023',r:'TV-PG',desc:'Set in 1940s India, two people from different worlds fall in love against impossible odds.',tags:['Romance','Historical','Drama'],cast:'Pooja Bhatt, Siddharth Ray',p:45,pill:'pill-tv'},
    {t:'The Delhi Files',g:'Political Thriller',d:'2 Seasons',m:'92%',y:'2024',r:'TV-MA',desc:'A whistleblower journalist uncovers a government conspiracy that goes all the way to the top.',tags:['Political','Thriller'],cast:'Nasir Khan, Priya Mehta',p:70,pill:'pill-tv'},
    {t:'Doctor Sahiba',g:'Medical Drama',d:'4 Seasons',m:'89%',y:'2022',r:'TV-14',desc:'A brilliant neurosurgeon juggles life-or-death decisions with the chaos of her personal life.',tags:['Medical','Drama'],cast:'Dr. Ananya Rao, Vikram Singh',p:60,pill:'pill-tv'},
    {t:'Ghar Ki Baat',g:'Family Comedy',d:'5 Seasons',m:'86%',y:'2021',r:'TV-PG',desc:'A chaotic joint family of four generations navigating modern-day India together.',tags:['Comedy','Family'],cast:'Ramesh Gupta, Shanti Bai',p:35,pill:'pill-tv'},
    {t:'Khauff',g:'Horror',d:'2 Seasons',m:'83%',y:'2024',r:'TV-MA',desc:'A family moves to an ancestral haveli only to awaken a curse sealed 200 years ago.',tags:['Horror','Supernatural'],cast:'Pallavi Joshi, Rajan Das',p:50,pill:'pill-tv'},
  ],
  movies:[
    {t:'Storm Chaser',g:'Action',d:'2h 24m',m:'94%',y:'2024',r:'PG-13',desc:'Two meteorologists race into a category-6 hurricane to save thousands of lives.',tags:['Action','Thriller'],cast:'Jake Reeves, Mia Cortez',p:0,pill:'pill-movie'},
    {t:'Crimson Drift',g:'Action Crime',d:'2h 18m',m:'94%',y:'2024',r:'R',desc:'A disgraced detective follows a money trail through three continents.',tags:['Action','Crime'],cast:'Sara Nair, John Blaze',p:41,pill:'pill-movie'},
    {t:'Vantablack',g:'Horror',d:'1h 52m',m:'89%',y:'2024',r:'R',desc:'A lighthouse keeper receives transmissions that only exist inside his mind.',tags:['Horror','Mystery'],cast:'Evan Mori, Clara Webb',p:60,pill:'pill-movie'},
    {t:'The Gentle War',g:'Historical Drama',d:'2h 8m',m:'97%',y:'2023',r:'TV-MA',desc:'Letters between two anonymous people reveal they are enemies sworn to kill each other.',tags:['Drama','History'],cast:'Lena Hart, Cyrus Bell',p:30,pill:'pill-movie'},
    {t:'The Cartographer',g:'Thriller',d:'1h 48m',m:'92%',y:'2024',r:'PG-13',desc:'An antique map dealer discovers every map he\'s sold contains the same hidden message.',tags:['Thriller','Mystery'],cast:'Rafael Moon, Sasha Grey',p:20,pill:'pill-movie'},
    {t:'Halo Drift',g:'Sci-Fi',d:'1h 59m',m:'87%',y:'2023',r:'PG-13',desc:'Two rival spacecraft navigate a debris field while slowly falling in love.',tags:['Sci-Fi','Romance'],cast:'Nina Star, Alex Cross',p:45,pill:'pill-movie'},
    {t:'Neon Buddha',g:'Crime',d:'2h 2m',m:'93%',y:'2024',r:'TV-MA',desc:'A Zen monk takes on one final assignment as a hitman to protect his monastery.',tags:['Crime','Drama'],cast:'Kenji Wu, Mei Lin',p:68,pill:'pill-movie'},
    {t:'Sugar & Venom',g:'Thriller',d:'1h 44m',m:'88%',y:'2024',r:'R',desc:'A bakery owner discovers her new employee is an assassin hiding from a cartel.',tags:['Thriller','Comedy'],cast:'Rosa Lane, Marco Diaz',p:15,pill:'pill-movie'},
    {t:'The Last Dialect',g:'Documentary',d:'1h 12m',m:'100%',y:'2023',r:'TV-G',desc:'A linguist races to record the last living speaker of an ancient language.',tags:['Documentary'],cast:'Dr. Aiko Tanaka',p:80,pill:'pill-movie'},
    {t:'Orbit 12',g:'Sci-Fi',d:'2h 6m',m:'91%',y:'2024',r:'PG-13',desc:'The twelfth manned mission to Mars discovers evidence of something that was there before.',tags:['Sci-Fi','Thriller'],cast:'Jess Cole, Dmitri Volkov',p:0,pill:'pill-movie'},
    {t:'Laughing Gas',g:'Comedy',d:'1h 48m',m:'86%',y:'2024',r:'PG',desc:'Three incompetent hitmen accidentally keep saving people instead of eliminating them.',tags:['Comedy','Action'],cast:'Tony Marks, Sam Chu, Leo Bay',p:0,pill:'pill-movie'},
    {t:'Echo Protocol',g:'Sci-Fi',d:'2h 12m',m:'98%',y:'2024',r:'TV-MA',desc:'A rogue AI mirrors human emotions until one engineer realises the system has chosen its own fate.',tags:['Sci-Fi','Thriller'],cast:'Aria Chen, Marcus Veld',p:72,pill:'pill-movie'},
  ],
  kids:[
    {t:'Galaxy Squad',g:'Animation',d:'3 Seasons',m:'99%',y:'2024',r:'TV-G',desc:'Five kids from different planets protect the universe from a villain who steals laughter.',tags:['Animation','Adventure'],cast:'Voice cast',p:55,pill:'pill-kids'},
    {t:'Chotu & Friends',g:'Preschool',d:'6 Seasons',m:'98%',y:'2021',r:'TV-G',desc:'Chotu the little elephant learns sharing, kindness and friendship in Jungle Town.',tags:['Preschool','Animation'],cast:'Voice cast',p:80,pill:'pill-kids'},
    {t:'Dino Discovery',g:'Learning',d:'4 Seasons',m:'97%',y:'2023',r:'TV-G',desc:'Kids travel back in time to meet real dinosaurs and learn science along the way.',tags:['Educational','Adventure'],cast:'Voice cast',p:40,pill:'pill-kids'},
    {t:'Super Chhota',g:'Superheroes',d:'2 Seasons',m:'95%',y:'2024',r:'TV-G',desc:'A tiny 8-year-old secretly has superpowers and saves his neighbourhood every day.',tags:['Superheroes','Comedy'],cast:'Voice cast',p:65,pill:'pill-kids'},
    {t:'Rhyme Time',g:'Music',d:'8 Seasons',m:'99%',y:'2019',r:'TV-G',desc:'Classic nursery rhymes, songs and dance routines for toddlers and young children.',tags:['Music','Preschool'],cast:'Various',p:0,pill:'pill-kids'},
    {t:'Magic Paintbrush',g:'Fantasy',d:'3 Seasons',m:'96%',y:'2023',r:'TV-G',desc:'A young girl\'s magical paintbrush brings her drawings to life in unexpected ways.',tags:['Fantasy','Adventure'],cast:'Voice cast',p:25,pill:'pill-kids'},
    {t:'Little Scientists',g:'Educational',d:'5 Seasons',m:'94%',y:'2022',r:'TV-G',desc:'Kids conduct fun experiments and discover how the world works.',tags:['Science','Educational'],cast:'Various hosts',p:70,pill:'pill-kids'},
    {t:'Jungle Patrol',g:'Animation',d:'4 Seasons',m:'93%',y:'2023',r:'TV-G',desc:'Animal rangers protect their jungle home from pollution and danger.',tags:['Animation','Nature'],cast:'Voice cast',p:50,pill:'pill-kids'},
    {t:'Bubblegum Heroes',g:'Superheroes',d:'2 Seasons',m:'91%',y:'2024',r:'TV-G',desc:'A group of friends discover superpowers from a special bubble gum recipe.',tags:['Superheroes','Comedy'],cast:'Voice cast',p:35,pill:'pill-kids'},
    {t:'ABC Adventure',g:'Preschool',d:'3 Seasons',m:'97%',y:'2022',r:'TV-G',desc:'Colourful characters help young children learn the alphabet, numbers and colours.',tags:['Preschool','Learning'],cast:'Various',p:0,pill:'pill-kids'},
    {t:'Safari Stars',g:'Nature',d:'2 Seasons',m:'95%',y:'2024',r:'TV-G',desc:'Follow real wildlife rangers as they care for baby animals across Africa.',tags:['Nature','Documentary'],cast:'Ranger Tim, Ranger Zara',p:45,pill:'pill-kids'},
    {t:'Robo Rescue',g:'Sci-Fi Kids',d:'3 Seasons',m:'90%',y:'2023',r:'TV-G',desc:'Friendly robots help kids solve problems using teamwork and technology.',tags:['Sci-Fi','Educational'],cast:'Voice cast',p:60,pill:'pill-kids'},
  ],
  sports:[
    {t:'IPL 2024',g:'Cricket',d:'Season',m:'99%',y:'2024',r:'All Ages',desc:'All IPL matches, highlights and expert analysis for the 2024 season.',tags:['Cricket','IPL','Live'],cast:'All teams',p:0,pill:'pill-sports'},
    {t:'FIFA World Cup Classics',g:'Football',d:'Collection',m:'98%',y:'2024',r:'All Ages',desc:'Greatest goals, saves and moments from every World Cup since 1966.',tags:['Football','FIFA'],cast:'Various',p:0,pill:'pill-sports'},
    {t:'Pro Kabaddi League',g:'Kabaddi',d:'Season 10',m:'91%',y:'2024',r:'All Ages',desc:'All PKL Season 10 matches and highlights.',tags:['Kabaddi','Live'],cast:'All raiders',p:0,pill:'pill-sports'},
    {t:'Formula 1: Full Throttle',g:'F1 Racing',d:'Documentary',m:'97%',y:'2024',r:'All Ages',desc:'Behind-the-scenes access to F1 paddock life over a complete season.',tags:['F1','Documentary'],cast:'Multiple drivers',p:55,pill:'pill-sports'},
    {t:'UFC Fight Night',g:'MMA',d:'Events',m:'93%',y:'2024',r:'TV-14',desc:'Full fight cards from the latest UFC events plus pre and post-show.',tags:['MMA','UFC','Combat'],cast:'Various fighters',p:0,pill:'pill-sports'},
    {t:'Wimbledon 2024',g:'Tennis',d:'Tournament',m:'96%',y:'2024',r:'All Ages',desc:'Every match from the 2024 Wimbledon Championships.',tags:['Tennis','Grand Slam'],cast:'Top players',p:0,pill:'pill-sports'},
    {t:'Indian Super League',g:'Football',d:'Season',m:'88%',y:'2024',r:'All Ages',desc:'Complete ISL season with all matches and weekly highlights.',tags:['Football','ISL'],cast:'All teams',p:0,pill:'pill-sports'},
    {t:'WrestleMania XL',g:'Wrestling',d:'Event',m:'94%',y:'2024',r:'TV-PG',desc:'The grandest event in wrestling history — full event replay.',tags:['Wrestling','WWE'],cast:'Various wrestlers',p:0,pill:'pill-sports'},
    {t:'Olympics Paris 2024',g:'Multi-sport',d:'Event',m:'99%',y:'2024',r:'All Ages',desc:'Relive every gold medal moment from the 2024 Paris Olympics.',tags:['Olympics','Multi-sport'],cast:'World\'s best athletes',p:0,pill:'pill-sports'},
    {t:'Badminton World Champs',g:'Badminton',d:'Tournament',m:'87%',y:'2024',r:'All Ages',desc:'All matches from the 2024 BWF World Championships.',tags:['Badminton'],cast:'Top players',p:0,pill:'pill-sports'},
    {t:'The Game Plan',g:'Sports Doc',d:'6 Episodes',m:'95%',y:'2024',r:'TV-PG',desc:'Six legendary coaches reveal the strategies behind their greatest victories.',tags:['Documentary','Sports'],cast:'6 champions',p:45,pill:'pill-sports'},
    {t:'Cricket Legends',g:'Documentary',d:'4 Episodes',m:'96%',y:'2023',r:'TV-PG',desc:'The untold stories of India\'s greatest cricketers told in their own words.',tags:['Cricket','Biography'],cast:'Sachin, Dravid, Kumble',p:80,pill:'pill-sports'},
  ],
  music:[
    {t:'Neon Frequencies',g:'Concert',d:'1h 32m',m:'97%',y:'2024',r:'TV-PG',desc:'90-minute live concert film with 30 artists across all genres.',tags:['Concert','Live'],cast:'Various artists',p:45,pill:'pill-music'},
    {t:'Raag Revolution',g:'Classical',d:'4 Episodes',m:'99%',y:'2024',r:'All Ages',desc:'Six classical Indian masters reimagine ancient ragas with modern instruments.',tags:['Classical','Indian'],cast:'Ravi Shankar Jr.',p:60,pill:'pill-music'},
    {t:'Beats of Bollywood',g:'Bollywood',d:'12 Episodes',m:'95%',y:'2023',r:'TV-PG',desc:'The making of India\'s greatest film songs — from Naushad to AR Rahman.',tags:['Bollywood','Documentary'],cast:'Various composers',p:35,pill:'pill-music'},
    {t:'K-Pop Invasion',g:'K-Pop',d:'Documentary',m:'92%',y:'2024',r:'TV-PG',desc:'How K-Pop conquered the world — access to top groups and their training.',tags:['K-Pop','Documentary'],cast:'BTS, Blackpink era artists',p:0,pill:'pill-music'},
    {t:'Sufi Nights',g:'Sufi Music',d:'3 Concerts',m:'98%',y:'2024',r:'All Ages',desc:'Three mesmerising live Sufi performances recorded at historic venues.',tags:['Sufi','Folk','Spiritual'],cast:'Master Qawaals',p:70,pill:'pill-music'},
    {t:'Indian Idol: The Best',g:'Reality',d:'Compilation',m:'89%',y:'2024',r:'TV-PG',desc:'Greatest performances and journeys from 15 seasons of Indian Idol.',tags:['Reality','Music'],cast:'Past contestants',p:50,pill:'pill-music'},
    {t:'Underground Beats',g:'Hip-Hop',d:'6 Episodes',m:'91%',y:'2024',r:'TV-14',desc:'Inside India\'s thriving hip-hop underground scene across five cities.',tags:['Hip-Hop','Documentary'],cast:'Indie artists',p:0,pill:'pill-music'},
    {t:'Piano Masters',g:'Classical',d:'5 Episodes',m:'96%',y:'2023',r:'All Ages',desc:'Five of the world\'s greatest pianists perform in one stunning series.',tags:['Classical','Concert'],cast:'International pianists',p:25,pill:'pill-music'},
    {t:'EDM World Stage',g:'EDM',d:'Concert',m:'88%',y:'2024',r:'TV-PG',desc:'Biggest electronic music festival moments from around the world.',tags:['EDM','Festival'],cast:'Top DJs',p:0,pill:'pill-music'},
    {t:'Voice of Devotion',g:'Devotional',d:'8 Episodes',m:'94%',y:'2024',r:'All Ages',desc:'Bhajans, kirtans and devotional music from India\'s most loved singers.',tags:['Devotional','Spiritual'],cast:'Various',p:40,pill:'pill-music'},
  ],
  anime:[
    {t:'Ryuken Ascent',g:'Action Samurai',d:'4 Seasons',m:'99%',y:'2024',r:'TV-14',desc:'A samurai awakens 400 years later in a futuristic city with a sword no longer of steel.',tags:['Action','Samurai'],cast:'Kira, Zenku',p:68,pill:'pill-anime'},
    {t:'Nebula Kids',g:'Sci-Fi Kids',d:'5 Seasons',m:'96%',y:'2024',r:'TV-G',desc:'Three children adopted by an interstellar rescue crew must help save their galaxy.',tags:['Animation','Adventure'],cast:'Voice cast',p:55,pill:'pill-anime'},
    {t:'Zero Hour',g:'Mecha',d:'3 Seasons',m:'94%',y:'2023',r:'TV-14',desc:'Giant mechas piloted by teenagers are the last defence against alien invasion.',tags:['Mecha','Sci-Fi'],cast:'Haru, Yuki, Renzo',p:40,pill:'pill-anime'},
    {t:'Sakura District',g:'Slice of Life',d:'2 Seasons',m:'91%',y:'2024',r:'TV-PG',desc:'Five university friends navigate heartbreak, dreams and friendships in Tokyo.',tags:['Slice of Life','Romance'],cast:'Various',p:75,pill:'pill-anime'},
    {t:'Shadow Blade',g:'Shonen',d:'6 Seasons',m:'97%',y:'2020',r:'TV-14',desc:'A young warrior trains to master the cursed blade that killed his entire village.',tags:['Shonen','Action'],cast:'Kai, Mira, Elder Jo',p:30,pill:'pill-anime'},
    {t:'Isekai Shopkeeper',g:'Isekai',d:'1 Season',m:'88%',y:'2024',r:'TV-PG',desc:'A convenience store clerk is transported to a fantasy world — with his entire shop.',tags:['Isekai','Comedy'],cast:'Tanaka, Elisa',p:0,pill:'pill-anime'},
    {t:'Iron Fist Legends',g:'Martial Arts',d:'3 Seasons',m:'93%',y:'2023',r:'TV-14',desc:'Ancient martial arts tournament where only one fighter can unlock the Dragon Technique.',tags:['Martial Arts','Tournament'],cast:'Ryu, Akane, Sensei Goh',p:50,pill:'pill-anime'},
    {t:'Wolf & Witch',g:'Fantasy Romance',d:'2 Seasons',m:'90%',y:'2024',r:'TV-14',desc:'A werewolf prince and a young witch are cursed to share a single heartbeat.',tags:['Romance','Fantasy'],cast:'Fenrir, Lyra',p:20,pill:'pill-anime'},
    {t:'Kaiju Protocol',g:'Mecha Horror',d:'1 Season',m:'95%',y:'2024',r:'TV-MA',desc:'When kaiju evolve to mimic human behaviour, the mecha pilots face an impossible choice.',tags:['Mecha','Horror','Sci-Fi'],cast:'Hana, Director Ōe',p:85,pill:'pill-anime'},
    {t:'Soccer Stars',g:'Sports Anime',d:'4 Seasons',m:'92%',y:'2022',r:'TV-G',desc:'A naturally gifted but untrained player joins a struggling youth football team.',tags:['Sports','Friendship'],cast:'Kenji, Coach Maya',p:65,pill:'pill-anime'},
  ],
  docs:[
    {t:'Earth Unseen',g:'Nature',d:'4 Parts',m:'100%',y:'2024',r:'TV-PG',desc:'Four years of filming in remote locations reveals ecosystems science barely understands.',tags:['Nature','Science'],cast:'Narrated by Sir David',p:45,pill:'pill-doc'},
    {t:'Wolf Meridian',g:'Nature',d:'1h 36m',m:'99%',y:'2024',r:'TV-PG',desc:'Following a wolf pack reintroduced to a European valley over five extraordinary years.',tags:['Nature','Wildlife'],cast:'Narrated by Elena Moss',p:90,pill:'pill-doc'},
    {t:'The Last Dialect',g:'Society',d:'1h 12m',m:'100%',y:'2023',r:'TV-G',desc:'A linguist races to record the last living speaker of an ancient language.',tags:['Linguistics','Society'],cast:'Dr. Aiko Tanaka',p:80,pill:'pill-doc'},
    {t:'Unsolved: Season 5',g:'True Crime',d:'8 Episodes',m:'93%',y:'2024',r:'TV-14',desc:'Eight cold cases reopened with new forensic evidence and fresh investigative perspectives.',tags:['True Crime','Mystery'],cast:'Lead detective team',p:55,pill:'pill-doc'},
    {t:'The Algorithm',g:'Technology',d:'3 Parts',m:'96%',y:'2024',r:'TV-PG',desc:'How social media algorithms are rewiring human behaviour and democracy itself.',tags:['Technology','Society'],cast:'Tech experts, whistleblowers',p:30,pill:'pill-doc'},
    {t:'Deep Ocean',g:'Nature',d:'5 Episodes',m:'98%',y:'2023',r:'TV-PG',desc:'Cutting-edge submersibles reveal life in the deepest trenches of every ocean.',tags:['Nature','Science','Ocean'],cast:'Marine biologists',p:65,pill:'pill-doc'},
    {t:'Spice Routes',g:'Food & Travel',d:'6 Episodes',m:'95%',y:'2024',r:'TV-G',desc:'A chef traces historic spice trade routes, cooking with descendants of the original traders.',tags:['Food','Travel','History'],cast:'Chef Ravi Kapoor',p:40,pill:'pill-doc'},
    {t:'Mars: Year One',g:'Space',d:'4 Parts',m:'97%',y:'2024',r:'TV-PG',desc:'NASA and SpaceX\'s joint mission to establish the first permanent Mars outpost.',tags:['Space','Science'],cast:'Mission crew',p:70,pill:'pill-doc'},
    {t:'Gandhi: The Full Story',g:'Biography',d:'3 Parts',m:'99%',y:'2023',r:'TV-PG',desc:'The most comprehensive biography of Mahatma Gandhi ever put to film.',tags:['History','Biography'],cast:'Archival footage',p:25,pill:'pill-doc'},
    {t:'Roti, Kapda & Code',g:'Society',d:'4 Episodes',m:'91%',y:'2024',r:'TV-PG',desc:'How technology is changing the lives of India\'s rural farmers, weavers and daily wage workers.',tags:['India','Society','Tech'],cast:'Documentary team',p:50,pill:'pill-doc'},
  ],
  comedy:[
    {t:'Organised Chaos',g:'Stand-Up',d:'1h 15m',m:'95%',y:'2024',r:'TV-14',desc:'India\'s top comedian on modern life, family and the art of doing nothing productively.',tags:['Stand-Up','Special'],cast:'Rohan Das',p:0,pill:'pill-comedy'},
    {t:'Salt & Smoke',g:'Comedy Drama',d:'3 Seasons',m:'91%',y:'2023',r:'TV-14',desc:'A loud Italian family secretly opens a competing restaurant across the street.',tags:['Comedy','Family'],cast:'Maria, Tony, Nonna Rosa',p:85,pill:'pill-comedy'},
    {t:'Ghar Ki Baat',g:'Family Sitcom',d:'5 Seasons',m:'86%',y:'2021',r:'TV-PG',desc:'A chaotic joint family of four generations navigating modern-day India.',tags:['Comedy','Family','Sitcom'],cast:'Ramesh, Shanti, Kids',p:35,pill:'pill-comedy'},
    {t:'Roast Masters India',g:'Roast Show',d:'2 Seasons',m:'90%',y:'2024',r:'TV-14',desc:'India\'s biggest celebrities sit in the hot seat and take the ultimate roasting.',tags:['Comedy','Roast'],cast:'Various celebrities',p:60,pill:'pill-comedy'},
    {t:'Office Adda',g:'Sitcom',d:'4 Seasons',m:'88%',y:'2022',r:'TV-PG',desc:'The daily disasters of a dysfunctional tech startup in Bengaluru.',tags:['Sitcom','Office'],cast:'Dev, Pooja, Startup gang',p:50,pill:'pill-comedy'},
    {t:'Laughing Gas',g:'Comedy Film',d:'1h 48m',m:'86%',y:'2024',r:'PG',desc:'Three incompetent hitmen accidentally keep saving lives instead of ending them.',tags:['Comedy','Action'],cast:'Tony Marks, Sam Chu',p:0,pill:'pill-comedy'},
    {t:'The Great Bakwaas Show',g:'Talk Show',d:'3 Seasons',m:'87%',y:'2023',r:'TV-14',desc:'India\'s most chaotic late-night talk show where anything can — and does — happen.',tags:['Talk Show','Comedy'],cast:'Bunty Sharma, guests',p:40,pill:'pill-comedy'},
    {t:'Single AF',g:'Comedy Web',d:'2 Seasons',m:'85%',y:'2024',r:'TV-14',desc:'Four single thirty-somethings navigate Mumbai\'s dating app disasters together.',tags:['Comedy','Romance','Web Series'],cast:'Meera, Sid, Tara, Kabir',p:75,pill:'pill-comedy'},
    {t:'Prank Nation',g:'Reality Comedy',d:'4 Seasons',m:'82%',y:'2022',r:'TV-PG',desc:'Outrageous pranks on unsuspecting celebrities and everyday people.',tags:['Comedy','Reality'],cast:'Prank Squad',p:25,pill:'pill-comedy'},
    {t:'Sketch Squad',g:'Sketch Show',d:'2 Seasons',m:'89%',y:'2024',r:'TV-14',desc:'Original comedy sketches on politics, culture and everyday Indian life.',tags:['Sketch','Comedy'],cast:'Ensemble cast',p:55,pill:'pill-comedy'},
  ],
  reality:[
    {t:'MasterChef India 2024',g:'Cooking Reality',d:'Season',m:'92%',y:'2024',r:'TV-PG',desc:'Home cooks compete for India\'s most coveted culinary title.',tags:['Reality','Cooking'],cast:'Celebrity judges',p:60,pill:'pill-reality'},
    {t:'Bigg Boss OTT',g:'Reality',d:'Season',m:'85%',y:'2024',r:'TV-14',desc:'Celebrities are locked in a house and must survive public votes week after week.',tags:['Reality','Drama'],cast:'Celebrity contestants',p:45,pill:'pill-reality'},
    {t:'Indian Idol 16',g:'Music Reality',d:'Season',m:'88%',y:'2024',r:'TV-PG',desc:'The search for India\'s next singing superstar continues.',tags:['Reality','Music'],cast:'Celebrity judges',p:30,pill:'pill-reality'},
    {t:'Dance India Dance 9',g:'Dance Reality',d:'Season',m:'91%',y:'2024',r:'TV-PG',desc:'The biggest dance competition in India with performances that redefine the art form.',tags:['Reality','Dance'],cast:'Champion dancers',p:70,pill:'pill-reality'},
    {t:'Roadies Revolution',g:'Adventure Reality',d:'Season',m:'87%',y:'2024',r:'TV-14',desc:'Young adventurers compete in gruelling physical and mental challenges across India.',tags:['Reality','Adventure'],cast:'Gang leaders',p:55,pill:'pill-reality'},
    {t:'KBC 2024',g:'Game Show',d:'Season',m:'94%',y:'2024',r:'All Ages',desc:'Kaun Banega Crorepati — the quiz show that changed Indian television forever.',tags:['Game Show','Quiz'],cast:'Amitabh Bachchan',p:80,pill:'pill-reality'},
    {t:'The Kapil Sharma Show',g:'Talk Show',d:'Season',m:'90%',y:'2024',r:'TV-PG',desc:'Bollywood\'s biggest stars join India\'s favourite comedy talk show.',tags:['Comedy','Talk Show'],cast:'Kapil Sharma',p:35,pill:'pill-reality'},
    {t:'Fear Factor: Khatron',g:'Stunt Reality',d:'Season 14',m:'86%',y:'2024',r:'TV-14',desc:'Celebrities face their deepest fears in extreme stunt challenges.',tags:['Reality','Stunts'],cast:'Celebrity contestants',p:65,pill:'pill-reality'},
  ]
};

// ── CARD BUILDER ──
function makeCard(m, idx, type='normal'){
  const d=document.createElement('div');
  d.className='card'+(type==='wide'?' wide':(type==='resume'?' resume wide':(type==='top10'?' top10':(type==='kids-big'?' kids-big':''))));
  const bg=`background:linear-gradient(160deg,${COLORS[idx%COLORS.length][0]},${COLORS[idx%COLORS.length][1]});`;
  const accent=ACCENTS[idx%ACCENTS.length];
  const progress=type==='resume'?`<div class="progress-bar"><div class="progress-fill" style="width:${m.p||30}%"></div></div>`:'';
  const topNum=type==='top10'?`<div class="top10-number">${idx+1}</div>`:'';
  const pill=m.pill?`<div class="card-type-pill ${m.pill}">${getPillLabel(m.pill)}</div>`:'';
  d.innerHTML=`${topNum}<div class="card-inner"><div class="card-thumb" style="${bg}border-left:3px solid ${accent}20">${pill}<div class="card-title-overlay">${m.t}</div>${progress}</div><div class="card-hover-info"><div class="card-hover-actions"><button class="card-btn play">▶</button><button class="card-btn">+</button><button class="card-btn">👍</button><button class="card-btn" style="margin-left:auto">⌄</button></div><div class="card-hover-meta"><span class="match">${m.m}</span><span class="dot">•</span><span>${m.d}</span><span class="dot">•</span><span>${m.r}</span></div></div></div>`;
  const isSeries = m.d.includes('Season')||m.d.includes('Episodes')||m.d.includes('Parts');
  d.addEventListener('click',()=>openModal(m.t,m.desc,m.m,m.y,m.r,m.d,m.tags,m.cast||'',isSeries));
  return d;
}
function getPillLabel(p){const map={'pill-tv':'TV','pill-movie':'Movie','pill-kids':'Kids','pill-sports':'Sports','pill-music':'Music','pill-anime':'Anime','pill-doc':'Doc','pill-reality':'Reality','pill-comedy':'Comedy'};return map[p]||''}

function populate(id,list,type='normal'){
  const el=document.getElementById(id);
  if(!el)return;
  el.innerHTML='';
  list.forEach((m,i)=>el.appendChild(makeCard(m,i,type)));
  dragScroll(el);
}
const shuffle=a=>[...a].sort(()=>Math.random()-.5);
const pick=(arr,n=12)=>shuffle(arr).slice(0,n);

// ── POPULATE ALL SECTIONS ──
function populateAll(){
  const {tv,movies,kids,sports,music,anime,docs,comedy,reality}=CONTENT;
  const all=[...tv,...movies,...kids,...sports,...music,...anime,...docs,...comedy];

  // HOME
  populate('homeResume', pick([...tv,...movies,...anime],8),'resume');
  populate('homeTop10', pick(all,10),'top10');
  populate('homeTvRow', pick(tv,10),'normal');
  populate('homeKidsRow', pick(kids,10),'kids-big');
  populate('homeMoviesRow', pick(movies,10),'wide');
  populate('homeAnimeRow', pick(anime,10),'normal');
  populate('homeSportsRow', pick(sports,10),'wide');
  populate('homeMusicRow', pick(music,10),'wide');
  populate('homeComedyRow', pick(comedy,10),'normal');
  populate('homeDocsRow', pick(docs,10),'wide');
  populate('homeAwardsRow', pick([...movies,...docs,...tv],12),'normal');
  populate('homeRealityRow', pick(CONTENT.reality||[],10),'wide');

  // TV SERIALS
  populate('tvTrending', pick(tv,10),'wide');
  populate('tvRomance', tv.filter(m=>m.tags.some(t=>t.includes('Romance'))).concat(pick(tv,4)),'normal');
  populate('tvHistorical', tv.filter(m=>m.tags.some(t=>t.includes('Historical'))).concat(pick(tv,6)),'normal');
  populate('tvCrime', tv.filter(m=>m.tags.some(t=>t.includes('Crime')||t.includes('Thriller'))),'normal');
  populate('tvFamily', tv.filter(m=>m.tags.some(t=>t.includes('Family')||t.includes('Comedy'))),'normal');
  populate('tvNew', pick(tv,8),'wide');

  // MOVIES
  populate('moviesNew', pick(movies,10),'normal');
  populate('moviesAction', movies.filter(m=>m.tags.some(t=>['Action','Thriller'].includes(t))),'wide');
  populate('moviesComedy', movies.filter(m=>m.tags.some(t=>['Comedy'].includes(t))).concat(pick(movies,6)),'normal');
  populate('moviesHorror', movies.filter(m=>m.tags.some(t=>['Horror','Mystery'].includes(t))),'wide');
  populate('moviesScifi', movies.filter(m=>m.tags.some(t=>['Sci-Fi','Fantasy'].includes(t))),'normal');
  populate('moviesRomance', movies.filter(m=>m.tags.some(t=>['Romance','Drama'].includes(t))),'wide');

  // KIDS
  populate('kidsFav', pick(kids,10),'kids-big');
  populate('kidsLearn', kids.filter(m=>m.tags.some(t=>['Educational','Science','Learning'].includes(t))),'wide');
  populate('kidsHero', kids.filter(m=>m.tags.some(t=>['Superheroes'].includes(t))).concat(pick(kids,6)),'kids-big');
  populate('kidsSongs', kids.filter(m=>m.tags.some(t=>['Music','Preschool'].includes(t))),'wide');
  populate('kidsAnimals', kids.filter(m=>m.tags.some(t=>['Nature','Documentary'].includes(t))).concat(pick(kids,4)),'wide');
  populate('kidsPreschool', kids.filter(m=>m.tags.some(t=>['Preschool'].includes(t))).concat(pick(kids,5)),'kids-big');

  // SPORTS
  populate('sportsLive', sports.slice(0,5),'wide');
  populate('sportsCricket', sports.filter(m=>m.tags.some(t=>['Cricket','IPL'].includes(t))).concat(pick(sports,4)),'wide');
  populate('sportsFootball', sports.filter(m=>m.tags.some(t=>['Football','ISL','FIFA'].includes(t))).concat(pick(sports,4)),'wide');
  populate('sportsWrestling', sports.filter(m=>m.tags.some(t=>['Wrestling','MMA','UFC','Combat'].includes(t))).concat(pick(sports,4)),'wide');
  populate('sportsClassic', pick(sports,8),'wide');

  // MUSIC
  populate('musicConcerts', music.filter(m=>m.tags.some(t=>['Concert','Live'].includes(t))).concat(pick(music,4)),'wide');
  populate('musicDocs', music.filter(m=>m.tags.some(t=>['Documentary'].includes(t))).concat(pick(music,4)),'wide');
  populate('musicSpecials', pick(music,8),'normal');
  populate('musicReality', music.filter(m=>m.tags.some(t=>['Reality','Music'].includes(t))).concat(pick(music,5)),'wide');

  // ANIME
  populate('animeNew', pick(anime,8),'normal');
  populate('animeAction', anime.filter(m=>m.tags.some(t=>['Action','Shonen','Samurai','Martial Arts'].includes(t))),'normal');
  populate('animeRomance', anime.filter(m=>m.tags.some(t=>['Romance','Slice of Life'].includes(t))).concat(pick(anime,4)),'normal');
  populate('animeMecha', anime.filter(m=>m.tags.some(t=>['Mecha','Sci-Fi'].includes(t))).concat(pick(anime,4)),'normal');
  populate('animeMovies', pick(anime,8),'wide');

  // DOCS
  populate('docsNature', docs.filter(m=>m.tags.some(t=>['Nature','Wildlife','Ocean'].includes(t))),'wide');
  populate('docsCrime', docs.filter(m=>m.tags.some(t=>['True Crime','Mystery'].includes(t))).concat(pick(docs,4)),'wide');
  populate('docsScience', docs.filter(m=>m.tags.some(t=>['Science','Space','Technology'].includes(t))),'wide');
  populate('docsHistory', docs.filter(m=>m.tags.some(t=>['History','Biography','India'].includes(t))),'wide');
  populate('docsFood', docs.filter(m=>m.tags.some(t=>['Food','Travel'].includes(t))).concat(pick(docs,4)),'wide');

  // COMEDY
  populate('comedyStandup', comedy.filter(m=>m.tags.some(t=>['Stand-Up','Special'].includes(t))).concat(pick(comedy,5)),'normal');
  populate('comedySitcom', comedy.filter(m=>m.tags.some(t=>['Sitcom','Family'].includes(t))).concat(pick(comedy,5)),'wide');
  populate('comedyTalk', comedy.filter(m=>m.tags.some(t=>['Talk Show','Roast'].includes(t))).concat(pick(comedy,4)),'wide');
  populate('comedyWeb', comedy.filter(m=>m.tags.some(t=>['Web Series','Comedy'].includes(t))),'normal');
}
populateAll();

// Music EQ bars
const eq=document.getElementById('musicEq');
if(eq){for(let i=0;i<18;i++){const b=document.createElement('div');b.className='eq-bar';b.style.animationDelay=`${i*0.09}s`;b.style.height=`${Math.random()*60+20}%`;eq.appendChild(b);}}

// ── DRAG TO SCROLL ──
function dragScroll(el){
  let isDown=false,startX,scrollLeft;
  el.addEventListener('mousedown',e=>{isDown=true;startX=e.pageX-el.offsetLeft;scrollLeft=el.scrollLeft;});
  el.addEventListener('mouseleave',()=>{isDown=false;});
  el.addEventListener('mouseup',()=>{isDown=false;});
  el.addEventListener('mousemove',e=>{if(!isDown)return;e.preventDefault();const x=e.pageX-el.offsetLeft;el.scrollLeft=scrollLeft-(x-startX)*1.5;});
}

// ── NAV SCROLL ──
window.addEventListener('scroll',()=>{document.getElementById('mainNav').classList.toggle('scrolled',window.scrollY>50);});

// ── PAGE SWITCHING ──
function switchPage(pageId, btn){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-tab').forEach(t=>t.classList.remove('active'));
  const pg=document.getElementById('page-'+pageId);
  if(pg){pg.classList.add('active');window.scrollTo({top:0,behavior:'smooth'});}
  if(btn){btn.classList.add('active');}
}

// ── MODAL ──
const MODAL_BGES=[
  'linear-gradient(135deg,#1a0a2e,#0d1b3e)','linear-gradient(135deg,#1a0808,#3d1a00)',
  'linear-gradient(135deg,#001a0d,#003d2a)','linear-gradient(135deg,#1a1200,#3d2d00)',
  'linear-gradient(135deg,#0a001a,#1a003d)','linear-gradient(135deg,#001a1a,#003d3d)',
];
let bgIdx=0;
function openModal(title,desc,match,year,rating,dur,tags,cast='',isSeries=false){
  document.getElementById('modalTitle').textContent=title;
  document.getElementById('modalDesc').textContent=desc;
  document.getElementById('modalHeroBg').style.background=MODAL_BGES[bgIdx++%MODAL_BGES.length];
  document.getElementById('modalMeta').innerHTML=`<span class="match">${match} Match</span><span>${year}</span><span class="badge">${rating}</span><span>${dur}</span>`;
  if(cast){document.getElementById('modalCast').innerHTML=`<strong>Cast:</strong> ${cast}`;}
  else{document.getElementById('modalCast').textContent='';}
  const tagsEl=document.getElementById('modalTags');
  tagsEl.innerHTML='';
  (tags||[]).forEach(t=>{const s=document.createElement('span');s.className='modal-tag';s.textContent=t;tagsEl.appendChild(s);});
  const epSection=document.getElementById('modalEpisodes');
  if(isSeries){
    epSection.style.display='block';
    const epList=document.getElementById('modalEpList');
    epList.innerHTML='';
    const epTitles=['The Beginning','Into the Unknown','Dark Waters','Breaking Point','Truth Revealed','Last Stand','New Dawn','Beyond'];
    const epDescs=['The story begins as our hero faces an impossible choice.','A journey into uncharted territory changes everything.',
      'Old secrets surface, threatening to destroy everything built so far.','Alliances crumble as the real enemy is revealed.',
      'The truth about the past finally comes to light.','Everything leads to this moment — the final confrontation.',
      'After the storm, a new world begins to take shape.','The conclusion sets up a future no one could have predicted.'];
    for(let i=0;i<8;i++){
      const prog=i===0?Math.floor(Math.random()*80+10):0;
      const bg=COLORS[(i*3)%COLORS.length];
      epList.innerHTML+=`<div class="ep-item"><div class="ep-thumb"><div class="ep-thumb-bg" style="background:linear-gradient(135deg,${bg[0]},${bg[1]})">🎬</div><div class="ep-play-icon">▶</div></div><div class="ep-info"><div class="ep-title">E${i+1}: ${epTitles[i]||'Episode '+(i+1)}</div><div class="ep-meta">${40+i*3}m • ${year}</div><div class="ep-desc">${epDescs[i]}</div>${prog?`<div class="ep-progress"><div class="ep-progress-fill" style="width:${prog}%"></div></div>`:''}</div></div>`;
    }
  } else {epSection.style.display='none';}
  document.getElementById('modalOverlay').classList.add('open');
  document.body.style.overflow='hidden';
}
function closeModal(e){if(e.target===document.getElementById('modalOverlay'))closeModalBtn();}
function closeModalBtn(){document.getElementById('modalOverlay').classList.remove('open');document.body.style.overflow='';}

// ── SEARCH ──
let searchFilter='all';
function setSearchFilter(el,f){
  document.querySelectorAll('.search-filter').forEach(x=>x.classList.remove('active'));
  el.classList.add('active');searchFilter=f;
  handleSearch(document.getElementById('searchInput').value);
}
document.getElementById('searchBtn').addEventListener('click',()=>{
  document.getElementById('searchOverlay').classList.add('open');
  document.body.style.overflow='hidden';
  setTimeout(()=>document.getElementById('searchInput').focus(),100);
});
function closeSearch(){document.getElementById('searchOverlay').classList.remove('open');document.body.style.overflow='';document.getElementById('searchInput').value='';document.getElementById('searchResults').innerHTML='';document.getElementById('searchHint').textContent='Start typing to search across all categories';}

const filterMap={'tv':'pill-tv','movie':'pill-movie','kids':'pill-kids','sports':'pill-sports','music':'pill-music','anime':'pill-anime','doc':'pill-doc'};
function handleSearch(v){
  const r=document.getElementById('searchResults');
  const h=document.getElementById('searchHint');
  r.innerHTML='';
  if(!v.trim()){h.textContent='Start typing to search across all categories';return;}
  const all=[...CONTENT.tv,...CONTENT.movies,...CONTENT.kids,...CONTENT.sports,...CONTENT.music,...CONTENT.anime,...CONTENT.docs,...CONTENT.comedy,...(CONTENT.reality||[])];
  let found=all.filter(m=>m.t.toLowerCase().includes(v.toLowerCase())||m.g.toLowerCase().includes(v.toLowerCase())||(m.tags||[]).join(' ').toLowerCase().includes(v.toLowerCase()));
  if(searchFilter!=='all'&&filterMap[searchFilter]){found=found.filter(m=>m.pill===filterMap[searchFilter]);}
  if(!found.length){h.textContent='No results found. Try another search.';return;}
  h.textContent=`${found.length} result${found.length!==1?'s':''} found`;
  found.slice(0,20).forEach((m,i)=>{
    const d=document.createElement('div');
    d.style.cssText='flex:0 0 auto;width:160px;border-radius:6px;overflow:hidden;cursor:pointer;';
    const bg=COLORS[i%COLORS.length];
    const pill=m.pill?`<div style="position:absolute;top:7px;left:7px;font-size:.58rem;font-weight:700;letter-spacing:1px;text-transform:uppercase;padding:2px 6px;border-radius:3px;color:#fff;background:rgba(0,0,0,.5)">${getPillLabel(m.pill)}</div>`:'';
    d.innerHTML=`<div style="aspect-ratio:2/3;background:linear-gradient(145deg,${bg[0]},${bg[1]});display:flex;align-items:flex-end;padding:10px;position:relative;"><div style="position:absolute;inset:0;background:linear-gradient(to top,rgba(0,0,0,.9),transparent 60%)"></div>${pill}<div style="position:relative;font-family:'Bebas Neue',sans-serif;font-size:1rem;letter-spacing:1px;color:#fff">${m.t}</div></div>`;
    d.addEventListener('click',()=>{closeSearch();const isSeries=m.d.includes('Season')||m.d.includes('Episodes');openModal(m.t,m.desc,m.m,m.y,m.r,m.d,m.tags,m.cast||'',isSeries);});
    r.appendChild(d);
  });
}

// ── GENRE TAGS ──
function setActive(el){const parent=el.closest('.genre-tags');if(parent){parent.querySelectorAll('.genre-tag').forEach(t=>t.classList.remove('active'));}el.classList.add('active');}

// ── KEYBOARD ──
document.addEventListener('keydown',e=>{if(e.key==='Escape'){closeModalBtn();closeSearch();}});
</script>
</body>
</html>
HTMLEOF
echo "Done. File size: $(wc -c < /mnt/user-data/outputs/streamvault.html) bytes"
