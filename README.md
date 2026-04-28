<!DOCTYPE html>
<html lang="en" dir="ltr" data-theme="dark">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>FixIt — Premium Home Services</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700&family=Outfit:wght@300;400;500;600&family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet"/>
<style>
[data-theme="dark"]{
  --bg:#080810;--bg2:#0d0d18;--surface:#111120;--card:#13131f;--card2:#181828;
  --border:rgba(255,255,255,0.07);--border2:rgba(255,255,255,0.12);
  --text:#f0eee8;--text2:#c8c4bc;--muted:#6e6b7a;
  --glass:rgba(255,255,255,0.04);--glass2:rgba(255,255,255,0.08);
  --shadow:rgba(0,0,0,0.6);--input-bg:rgba(255,255,255,0.04);--nav-bg:rgba(8,8,16,0.85);
}
[data-theme="light"]{
  --bg:#f8f6f0;--bg2:#f0ede5;--surface:#ffffff;--card:#ffffff;--card2:#f5f2ec;
  --border:rgba(0,0,0,0.08);--border2:rgba(0,0,0,0.14);
  --text:#1a1825;--text2:#4a4760;--muted:#9492a0;
  --glass:rgba(255,255,255,0.7);--glass2:rgba(255,255,255,0.9);
  --shadow:rgba(0,0,0,0.12);--input-bg:rgba(0,0,0,0.03);--nav-bg:rgba(248,246,240,0.9);
}
:root{
  --gold:#c9a84c;--gold2:#e8c97a;--gold3:#f5e0a0;--amber:#d4831a;
  --teal:#1a9e8f;--rose:#c4405a;--blue:#2a6fd4;--warm:#c97040;--silver:#8a9ab0;--green:#2d9e5f;
  --font-display:'Playfair Display',serif;--font-body:'Outfit',sans-serif;--font-ar:'Cairo',sans-serif;
  --radius:4px;--ease:cubic-bezier(.25,.46,.45,.94);--ease-out:cubic-bezier(0,.55,.45,1);
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth;font-size:16px}
body{background:var(--bg);color:var(--text);font-family:var(--font-body);line-height:1.65;overflow-x:hidden;min-height:100vh;transition:background .4s,color .4s;}
[dir="rtl"] *{font-family:var(--font-ar)}
button{cursor:pointer;font-family:inherit}
a{text-decoration:none;color:inherit}

.ambient{position:fixed;inset:0;pointer-events:none;z-index:0;overflow:hidden}
.ambient-orb{position:absolute;border-radius:50%;filter:blur(120px);animation:orbFloat 20s ease-in-out infinite}
.orb1{width:700px;height:700px;top:-200px;left:-200px;background:radial-gradient(circle,rgba(201,168,76,.12) 0%,transparent 70%);animation-delay:0s}
.orb2{width:500px;height:500px;bottom:-100px;right:-100px;background:radial-gradient(circle,rgba(196,64,90,.08) 0%,transparent 70%);animation-delay:-7s}
.orb3{width:400px;height:400px;top:40%;left:50%;background:radial-gradient(circle,rgba(26,158,143,.07) 0%,transparent 70%);animation-delay:-14s}
@keyframes orbFloat{0%,100%{transform:translate(0,0) scale(1)}33%{transform:translate(40px,-30px) scale(1.05)}66%{transform:translate(-20px,20px) scale(.97)}}
[data-theme="light"] .orb1{background:radial-gradient(circle,rgba(201,168,76,.15) 0%,transparent 70%)}
[data-theme="light"] .orb2{background:radial-gradient(circle,rgba(196,64,90,.1) 0%,transparent 70%)}
.grain{position:fixed;inset:0;pointer-events:none;z-index:9998;opacity:.35;background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 512 512' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='g'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23g)' opacity='.05'/%3E%3C/svg%3E")}

nav{position:fixed;top:0;left:0;right:0;z-index:900;height:72px;display:flex;align-items:center;justify-content:space-between;padding:0 48px;background:var(--nav-bg);backdrop-filter:blur(24px) saturate(1.8);border-bottom:1px solid var(--border);transition:all .4s}
nav.scrolled{height:62px;box-shadow:0 8px 40px var(--shadow)}
.nav-logo{display:flex;align-items:baseline;gap:2px;font-family:var(--font-display);font-size:1.65rem;font-weight:700;letter-spacing:-.5px;color:var(--text)}
.nav-logo .dot{width:8px;height:8px;border-radius:50%;background:linear-gradient(135deg,var(--gold),var(--amber));margin-bottom:4px;margin-left:2px;animation:pulse 2s ease-in-out infinite}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.6;transform:scale(.8)}}
[dir="rtl"] .nav-logo{font-family:var(--font-ar);font-weight:900;letter-spacing:0}
.nav-center{position:absolute;left:50%;transform:translateX(-50%);display:flex;gap:36px}
.nav-center a{font-size:.8rem;font-weight:500;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted);padding:4px 0;border-bottom:2px solid transparent;transition:color .25s,border-color .25s}
[dir="rtl"] .nav-center a{letter-spacing:0;text-transform:none;font-size:.9rem}
.nav-center a:hover,.nav-center a.active{color:var(--text);border-color:var(--gold)}
.nav-actions{display:flex;align-items:center;gap:10px}
.btn-nav-lang{height:36px;padding:0 16px;background:var(--glass);border:1px solid var(--border2);color:var(--text2);font-size:.75rem;font-weight:600;letter-spacing:1px;display:flex;align-items:center;gap:6px;border-radius:var(--radius);transition:all .2s}
.btn-nav-lang:hover{background:var(--glass2);color:var(--text)}
.btn-nav-theme{width:36px;height:36px;background:var(--glass);border:1px solid var(--border2);color:var(--text2);font-size:1rem;display:flex;align-items:center;justify-content:center;border-radius:var(--radius);transition:all .2s}
.btn-nav-theme:hover{background:var(--glass2);color:var(--text)}
.btn-nav-cta{height:36px;padding:0 24px;background:linear-gradient(135deg,var(--gold),var(--amber));border:none;color:#1a1200;font-size:.8rem;font-weight:700;letter-spacing:.5px;border-radius:var(--radius);transition:all .25s;white-space:nowrap;box-shadow:0 2px 16px rgba(201,168,76,.3)}
.btn-nav-cta:hover{transform:translateY(-2px);box-shadow:0 6px 24px rgba(201,168,76,.45)}
.nav-hamburger{display:none;flex-direction:column;gap:5px;background:none;border:none;padding:4px}
.nav-hamburger span{display:block;width:22px;height:2px;background:var(--text);border-radius:2px;transition:.3s}

.hero{position:relative;min-height:100vh;display:flex;flex-direction:column;justify-content:center;padding:140px 48px 100px;overflow:hidden}
.hero-bg-lines{position:absolute;inset:0;background-image:linear-gradient(to right,var(--border) 1px,transparent 1px),linear-gradient(to bottom,var(--border) 1px,transparent 1px);background-size:80px 80px;opacity:.5;mask-image:radial-gradient(ellipse 90% 90% at 30% 30%,black 30%,transparent 80%)}
.hero-eyebrow{display:inline-flex;align-items:center;gap:10px;margin-bottom:32px;animation:reveal .8s both}
.hero-eyebrow-line{width:40px;height:1px;background:linear-gradient(90deg,var(--gold),transparent)}
.hero-eyebrow-text{font-size:.7rem;font-weight:600;letter-spacing:3px;text-transform:uppercase;color:var(--gold)}
[dir="rtl"] .hero-eyebrow-text{letter-spacing:0;text-transform:none}
[dir="rtl"] .hero-eyebrow{flex-direction:row-reverse}
.hero-title{font-family:var(--font-display);font-size:clamp(3.5rem,8vw,8rem);font-weight:900;line-height:.95;letter-spacing:-2px;max-width:900px;animation:reveal .8s .1s both}
[dir="rtl"] .hero-title{font-family:var(--font-ar);font-weight:900;font-size:clamp(2.5rem,7vw,6rem);line-height:1.15;letter-spacing:0}
.hero-title .line1{display:block;color:var(--text)}
.hero-title .line2{display:block;background:linear-gradient(135deg,var(--gold) 0%,var(--gold2) 40%,var(--amber) 100%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.hero-title .line3{display:block;color:transparent;-webkit-text-stroke:1px var(--muted);font-style:italic}
[dir="rtl"] .hero-title .line3{-webkit-text-stroke:0;color:var(--gold)}
.hero-sub{margin-top:28px;font-size:1.1rem;font-weight:300;color:var(--text2);max-width:520px;line-height:1.75;animation:reveal .8s .2s both}
.hero-ctas{margin-top:44px;display:flex;gap:14px;flex-wrap:wrap;animation:reveal .8s .3s both}
.btn-hero-primary{height:54px;padding:0 36px;background:linear-gradient(135deg,var(--gold),var(--amber));border:none;color:#120e00;font-size:.9rem;font-weight:700;letter-spacing:.5px;border-radius:var(--radius);display:flex;align-items:center;gap:10px;transition:all .3s;box-shadow:0 4px 24px rgba(201,168,76,.35)}
.btn-hero-primary:hover{transform:translateY(-3px);box-shadow:0 10px 40px rgba(201,168,76,.5)}
.btn-hero-primary svg{transition:transform .3s}
.btn-hero-primary:hover svg{transform:translateX(4px)}
.btn-hero-secondary{height:54px;padding:0 36px;background:transparent;border:1px solid var(--border2);color:var(--text);font-size:.9rem;font-weight:500;border-radius:var(--radius);display:flex;align-items:center;gap:10px;transition:all .3s;backdrop-filter:blur(8px)}
.btn-hero-secondary:hover{background:var(--glass2);border-color:var(--gold);transform:translateY(-3px)}
.hero-stats{margin-top:80px;display:flex;border:1px solid var(--border);max-width:640px;border-radius:var(--radius);overflow:hidden;animation:reveal .8s .4s both;backdrop-filter:blur(12px);background:var(--glass)}
.hero-stat{flex:1;padding:22px 24px;border-right:1px solid var(--border);text-align:center}
.hero-stat:last-child{border-right:none}
.hero-stat-val{font-family:var(--font-display);font-size:1.8rem;font-weight:700;background:linear-gradient(135deg,var(--gold),var(--gold2));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;line-height:1;margin-bottom:4px}
[dir="rtl"] .hero-stat-val{font-family:var(--font-ar)}
.hero-stat-lbl{font-size:.65rem;font-weight:500;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted)}
[dir="rtl"] .hero-stat-lbl{letter-spacing:0;text-transform:none}
.hero-scroll{position:absolute;bottom:36px;left:50%;transform:translateX(-50%);display:flex;flex-direction:column;align-items:center;gap:8px;color:var(--muted);font-size:.65rem;letter-spacing:2px;text-transform:uppercase;animation:reveal 1s .6s both}
.scroll-line{width:1px;height:48px;background:linear-gradient(to bottom,var(--gold),transparent);animation:scrollPulse 2s ease-in-out infinite}
@keyframes scrollPulse{0%,100%{opacity:.3}50%{opacity:1}}
.hero-deco{position:absolute;right:8%;top:25%;width:380px;height:380px;border:1px solid var(--border);border-radius:50%;display:flex;align-items:center;justify-content:center;animation:decoSpin 40s linear infinite;opacity:.5}
.hero-deco-inner{width:260px;height:260px;border:1px solid var(--border2);border-radius:50%;display:flex;align-items:center;justify-content:center;animation:decoSpin 25s linear infinite reverse}
.hero-deco-core{width:160px;height:160px;background:radial-gradient(circle,rgba(201,168,76,.15),transparent);border:1px solid rgba(201,168,76,.2);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:3.5rem}
@keyframes decoSpin{from{transform:rotate(0deg)}to{transform:rotate(360deg)}}

.search-section{position:relative;z-index:1;padding:0 48px 90px}
.search-wrapper{max-width:760px;background:var(--surface);border:1px solid var(--border2);border-radius:var(--radius);display:flex;align-items:center;overflow:hidden;box-shadow:0 8px 48px var(--shadow);transition:box-shadow .3s}
.search-wrapper:focus-within{box-shadow:0 8px 48px var(--shadow),0 0 0 2px rgba(201,168,76,.3)}
.search-icon{padding:0 18px;color:var(--muted);font-size:1.1rem;flex-shrink:0}
.search-input{flex:1;background:transparent;border:none;outline:none;padding:18px 0;color:var(--text);font-family:var(--font-body);font-size:.95rem}
[dir="rtl"] .search-input{font-family:var(--font-ar);text-align:right}
.search-input::placeholder{color:var(--muted)}
.search-divider{width:1px;height:28px;background:var(--border2);flex-shrink:0}
.search-loc{background:transparent;border:none;outline:none;padding:18px 20px;color:var(--muted);font-family:var(--font-body);font-size:.85rem;cursor:pointer;flex-shrink:0}
[dir="rtl"] .search-loc{font-family:var(--font-ar)}
.search-loc option{background:var(--surface)}
.search-btn{height:100%;padding:0 28px;background:linear-gradient(135deg,var(--gold),var(--amber));border:none;color:#120e00;font-size:.8rem;font-weight:700;letter-spacing:.5px;display:flex;align-items:center;gap:8px;transition:all .25s;white-space:nowrap;flex-shrink:0}
.search-btn:hover{filter:brightness(1.1)}

.section{position:relative;z-index:1;padding:100px 48px}
.section-header{margin-bottom:60px}
.section-kicker{display:inline-flex;align-items:center;gap:10px;font-size:.7rem;font-weight:600;letter-spacing:3px;text-transform:uppercase;color:var(--gold);margin-bottom:14px}
[dir="rtl"] .section-kicker{letter-spacing:0;text-transform:none;flex-direction:row-reverse}
.section-kicker-line{width:30px;height:1px;background:var(--gold)}
.section-title{font-family:var(--font-display);font-size:clamp(2rem,4vw,3.2rem);font-weight:700;line-height:1.1;letter-spacing:-.5px}
[dir="rtl"] .section-title{font-family:var(--font-ar);font-weight:900;letter-spacing:0;line-height:1.3}
.section-sub{margin-top:14px;font-size:1rem;color:var(--text2);font-weight:300;max-width:520px;line-height:1.7}

.services-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}
.svc-card{position:relative;overflow:hidden;background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:36px 32px;cursor:pointer;transition:transform .35s,border-color .35s,box-shadow .35s}
.svc-card::before{content:'';position:absolute;inset:0;background:linear-gradient(135deg,var(--svc-color,transparent)14%,transparent 55%);opacity:0;transition:opacity .4s}
.svc-card:hover::before{opacity:1}
.svc-card:hover{transform:translateY(-6px);border-color:var(--svc-color,var(--border));box-shadow:0 20px 60px -10px color-mix(in srgb,var(--svc-color) 25%,transparent)}
.svc-card[data-s="electrician"]{--svc-color:#c9a84c}
.svc-card[data-s="plumber"]{--svc-color:#2a6fd4}
.svc-card[data-s="carpenter"]{--svc-color:#c97040}
.svc-card[data-s="blacksmith"]{--svc-color:#8a9ab0}
.svc-card[data-s="painter"]{--svc-color:#c4405a}
.svc-card[data-s="construction"]{--svc-color:#2d9e5f}
.svc-num{position:absolute;top:20px;right:24px;font-family:var(--font-display);font-size:4rem;font-weight:900;color:var(--border);line-height:1;transition:color .35s,opacity .35s}
[dir="rtl"] .svc-num{right:auto;left:24px}
.svc-card:hover .svc-num{color:var(--svc-color);opacity:.18}
.svc-icon-wrap{width:56px;height:56px;background:linear-gradient(135deg,color-mix(in srgb,var(--svc-color) 20%,transparent),transparent);border:1px solid color-mix(in srgb,var(--svc-color) 30%,transparent);border-radius:var(--radius);display:flex;align-items:center;justify-content:center;font-size:1.6rem;margin-bottom:22px;transition:transform .35s}
.svc-card:hover .svc-icon-wrap{transform:scale(1.1) rotate(-5deg)}
.svc-name{font-family:var(--font-display);font-size:1.4rem;font-weight:700;margin-bottom:10px;line-height:1.2}
[dir="rtl"] .svc-name{font-family:var(--font-ar);font-weight:900;font-size:1.2rem}
.svc-desc{font-size:.85rem;color:var(--text2);font-weight:300;line-height:1.7;margin-bottom:22px}
.svc-footer{display:flex;align-items:center;justify-content:space-between}
.svc-price{font-size:.75rem;font-weight:600;color:var(--svc-color);letter-spacing:.5px}
.svc-arrow{width:34px;height:34px;border:1px solid var(--border2);border-radius:50%;display:flex;align-items:center;justify-content:center;color:var(--muted);font-size:.9rem;transition:all .3s}
.svc-card:hover .svc-arrow{background:var(--svc-color);border-color:var(--svc-color);color:#fff;transform:translateX(3px)}
[dir="rtl"] .svc-card:hover .svc-arrow{transform:translateX(-3px)}

.emp-section{background:var(--bg2);border-top:1px solid var(--border);border-bottom:1px solid var(--border)}
.filter-bar{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:44px;padding-bottom:24px;border-bottom:1px solid var(--border)}
.filter-pill{height:34px;padding:0 18px;background:var(--glass);border:1px solid var(--border);color:var(--muted);font-size:.75rem;font-weight:500;letter-spacing:.5px;border-radius:20px;transition:all .25s}
[dir="rtl"] .filter-pill{font-family:var(--font-ar)}
.filter-pill.active,.filter-pill:hover{background:linear-gradient(135deg,var(--gold),var(--amber));border-color:transparent;color:#120e00;font-weight:700}
.emp-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:20px}
.emp-card{position:relative;background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:28px;transition:transform .3s,border-color .3s,box-shadow .3s;overflow:hidden}
.emp-card::after{content:'';position:absolute;inset:0;background:linear-gradient(160deg,rgba(201,168,76,.04) 0%,transparent 50%);opacity:0;transition:opacity .3s;pointer-events:none}
.emp-card:hover::after{opacity:1}
.emp-card:hover{transform:translateY(-5px);border-color:var(--border2);box-shadow:0 20px 60px -12px var(--shadow)}
.emp-availability{position:absolute;top:20px;right:20px;display:flex;align-items:center;gap:5px;font-size:.65rem;font-weight:600;letter-spacing:1px;text-transform:uppercase}
[dir="rtl"] .emp-availability{right:auto;left:20px;flex-direction:row-reverse}
.avail-dot{width:7px;height:7px;border-radius:50%;flex-shrink:0}
.avail-dot.on{background:#27c97a;box-shadow:0 0 6px rgba(39,201,122,.5)}
.avail-dot.off{background:#e05050}
.emp-top{display:flex;gap:14px;margin-bottom:18px}
.emp-ava{width:54px;height:54px;border-radius:50%;flex-shrink:0;display:flex;align-items:center;justify-content:center;font-size:1.5rem;border:2px solid var(--border2);position:relative}
.emp-ava-ring{position:absolute;inset:-4px;border-radius:50%;border:1px solid;opacity:0;transition:opacity .3s}
.emp-card:hover .emp-ava-ring{opacity:1}
.emp-name-block{flex:1;padding-top:2px}
.emp-name{font-size:1rem;font-weight:600;margin-bottom:2px}
.emp-trade-text{font-size:.72rem;font-weight:500;letter-spacing:.5px;color:var(--muted)}
[dir="rtl"] .emp-trade-text{letter-spacing:0}
.emp-loc{display:inline-flex;align-items:center;gap:4px;font-size:.7rem;color:var(--muted);margin-top:4px}
.emp-stars-row{display:flex;align-items:center;gap:8px;margin-bottom:14px}
.emp-stars-visual{display:flex;gap:2px}
.emp-star{font-size:.75rem;color:var(--border2)}
.emp-star.lit{color:var(--gold)}
.emp-star.half{color:var(--gold);opacity:.5}
.emp-rating-num{font-size:.85rem;font-weight:700;color:var(--text)}
.emp-rating-count{font-size:.75rem;color:var(--muted)}
.emp-bio{font-size:.82rem;color:var(--text2);line-height:1.65;margin-bottom:18px}
.emp-bottom{display:flex;align-items:center;justify-content:space-between;padding-top:16px;border-top:1px solid var(--border)}
.emp-rate{display:flex;flex-direction:column}
.emp-rate-val{font-family:var(--font-display);font-size:1.5rem;font-weight:700;background:linear-gradient(135deg,var(--gold),var(--amber));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;line-height:1}
[dir="rtl"] .emp-rate-val{font-family:var(--font-ar)}
.emp-rate-lbl{font-size:.65rem;color:var(--muted);text-transform:uppercase;letter-spacing:.5px}
[dir="rtl"] .emp-rate-lbl{letter-spacing:0;text-transform:none}
.emp-btns{display:flex;gap:8px}
.emp-btn-outline{height:34px;padding:0 14px;background:transparent;border:1px solid var(--border2);color:var(--text2);font-size:.75rem;font-weight:500;border-radius:var(--radius);transition:all .2s}
.emp-btn-outline:hover{border-color:var(--gold);color:var(--gold)}
.emp-btn-fill{height:34px;padding:0 16px;background:linear-gradient(135deg,var(--gold),var(--amber));border:none;color:#120e00;font-size:.75rem;font-weight:700;border-radius:var(--radius);transition:all .2s}
.emp-btn-fill:hover{transform:translateY(-1px);filter:brightness(1.1)}

.how-grid{display:grid;grid-template-columns:repeat(4,1fr);position:relative}
.how-grid::before{content:'';position:absolute;top:38px;left:calc(12.5% + 20px);right:calc(12.5% + 20px);height:1px;background:linear-gradient(90deg,transparent,var(--gold),transparent);opacity:.4}
[dir="rtl"] .how-grid::before{background:linear-gradient(270deg,transparent,var(--gold),transparent)}
.how-step{padding:0 24px;text-align:center;position:relative}
.how-step-icon-wrap{width:76px;height:76px;background:var(--card);border:1px solid var(--border2);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.6rem;margin:0 auto 24px;position:relative;z-index:1;transition:all .3s}
.how-step:hover .how-step-icon-wrap{border-color:var(--gold);box-shadow:0 0 0 4px rgba(201,168,76,.15);transform:scale(1.08)}
.how-step-title{font-family:var(--font-display);font-size:1.05rem;font-weight:700;margin-bottom:10px}
[dir="rtl"] .how-step-title{font-family:var(--font-ar);font-weight:900}
.how-step-desc{font-size:.82rem;color:var(--text2);line-height:1.7;font-weight:300}

.reviews-section{background:var(--bg2);border-top:1px solid var(--border)}
.reviews-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:20px}
.review-card{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:30px;transition:transform .3s,border-color .3s;position:relative;overflow:hidden}
.review-card::before{content:'\201C';position:absolute;top:-10px;left:20px;font-family:var(--font-display);font-size:6rem;font-weight:900;color:var(--gold);opacity:.1;line-height:1}
.review-card:hover{transform:translateY(-4px);border-color:rgba(201,168,76,.2)}
.review-stars-row{display:flex;gap:2px;margin-bottom:14px}
.review-star{font-size:.8rem;color:var(--gold)}
.review-text{font-size:.875rem;color:var(--text2);line-height:1.75;font-style:italic;font-weight:300;margin-bottom:20px;position:relative;z-index:1}
.review-author-row{display:flex;align-items:center;gap:12px}
.review-author-avatar{width:38px;height:38px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.1rem;background:linear-gradient(135deg,rgba(201,168,76,.2),rgba(212,131,26,.2));border:1px solid rgba(201,168,76,.2);flex-shrink:0}
.review-author-name{font-size:.85rem;font-weight:600;margin-bottom:1px}
.review-author-role{font-size:.72rem;color:var(--muted)}

.trust-banner{padding:60px 48px;background:linear-gradient(135deg,color-mix(in srgb,var(--gold) 8%,var(--card)),var(--card));border-top:1px solid var(--border);border-bottom:1px solid var(--border)}
.trust-items{display:flex;justify-content:space-around;align-items:center}
.trust-item{display:flex;flex-direction:column;align-items:center;gap:10px;flex:1;border-right:1px solid var(--border);padding:0 24px;text-align:center}
.trust-item:last-child{border-right:none}
[dir="rtl"] .trust-item{border-right:none;border-left:1px solid var(--border)}
[dir="rtl"] .trust-item:last-child{border-left:none}
.trust-icon{font-size:1.8rem}
.trust-label{font-size:.78rem;font-weight:500;color:var(--text2)}

footer{background:var(--bg);border-top:1px solid var(--border);padding:80px 48px 40px;position:relative;z-index:1}
.footer-top{display:grid;grid-template-columns:2.2fr 1fr 1fr 1fr;gap:48px;margin-bottom:60px}
.footer-brand{font-family:var(--font-display);font-size:2rem;font-weight:700;letter-spacing:-.5px;margin-bottom:14px;background:linear-gradient(135deg,var(--gold),var(--gold2));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
[dir="rtl"] .footer-brand{font-family:var(--font-ar);font-weight:900;letter-spacing:0}
.footer-tagline{font-size:.85rem;color:var(--muted);font-weight:300;line-height:1.7;max-width:260px;margin-bottom:24px}
.footer-social{display:flex;gap:10px}
.social-btn{width:34px;height:34px;background:var(--glass);border:1px solid var(--border2);border-radius:var(--radius);display:flex;align-items:center;justify-content:center;font-size:.8rem;color:var(--muted);transition:all .2s}
.social-btn:hover{background:var(--gold);border-color:var(--gold);color:#120e00}
.footer-col-title{font-size:.7rem;font-weight:700;letter-spacing:2px;text-transform:uppercase;color:var(--muted);margin-bottom:18px}
[dir="rtl"] .footer-col-title{letter-spacing:0;text-transform:none}
.footer-links{list-style:none;display:flex;flex-direction:column;gap:10px}
.footer-links li a,.footer-links li button{font-size:.85rem;color:var(--text2);background:none;border:none;padding:0;cursor:pointer;font-family:inherit;transition:color .2s;display:flex;align-items:center;gap:6px}
.footer-links li a:hover,.footer-links li button:hover{color:var(--gold)}
.footer-bottom{border-top:1px solid var(--border);padding-top:28px;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px}
.footer-copy{font-size:.78rem;color:var(--muted)}
.footer-badges{display:flex;gap:8px}
.footer-badge{height:26px;padding:0 12px;background:var(--glass);border:1px solid var(--border);border-radius:20px;font-size:.65rem;font-weight:600;letter-spacing:.5px;text-transform:uppercase;color:var(--muted);display:flex;align-items:center;gap:5px}

.overlay{display:none;position:fixed;inset:0;z-index:1000;background:rgba(4,4,10,.85);backdrop-filter:blur(12px);align-items:center;justify-content:center;padding:20px}
.overlay.open{display:flex}
.modal{background:var(--surface);border:1px solid var(--border2);border-radius:calc(var(--radius)*2);width:100%;max-width:580px;max-height:92vh;overflow-y:auto;padding:48px;position:relative;animation:modalIn .35s var(--ease-out) both;box-shadow:0 40px 100px rgba(0,0,0,.5)}
.modal-wide{max-width:680px}
@keyframes modalIn{from{opacity:0;transform:translateY(24px) scale(.97)}to{opacity:1;transform:translateY(0) scale(1)}}
.modal-close{position:absolute;top:20px;right:20px;width:32px;height:32px;background:var(--glass);border:1px solid var(--border);border-radius:50%;color:var(--muted);font-size:1rem;display:flex;align-items:center;justify-content:center;transition:all .2s;z-index:1}
[dir="rtl"] .modal-close{right:auto;left:20px}
.modal-close:hover{background:var(--rose);border-color:var(--rose);color:#fff}
.modal-eyebrow{display:inline-flex;align-items:center;gap:8px;font-size:.65rem;font-weight:700;letter-spacing:2px;text-transform:uppercase;color:var(--gold);margin-bottom:10px}
[dir="rtl"] .modal-eyebrow{letter-spacing:0;text-transform:none}
.modal-title{font-family:var(--font-display);font-size:1.9rem;font-weight:700;letter-spacing:-.3px;margin-bottom:6px}
[dir="rtl"] .modal-title{font-family:var(--font-ar);font-weight:900;letter-spacing:0;font-size:1.6rem}
.modal-sub{font-size:.85rem;color:var(--text2);margin-bottom:32px;font-weight:300}
.form-group{margin-bottom:20px}
.form-label{display:block;font-size:.7rem;font-weight:600;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted);margin-bottom:8px}
[dir="rtl"] .form-label{letter-spacing:0;text-transform:none;text-align:right}
.form-control{width:100%;padding:13px 16px;background:var(--input-bg);border:1px solid var(--border2);border-radius:var(--radius);color:var(--text);font-family:var(--font-body);font-size:.9rem;outline:none;transition:border-color .25s,box-shadow .25s}
[dir="rtl"] .form-control{font-family:var(--font-ar);text-align:right}
.form-control:focus{border-color:var(--gold);box-shadow:0 0 0 3px rgba(201,168,76,.15)}
.form-control::placeholder{color:var(--muted)}
textarea.form-control{resize:vertical;min-height:100px}
select.form-control option{background:var(--surface)}
.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px}
.price-wrap{display:flex;align-items:center;gap:8px}
.price-symbol{font-size:1.1rem;color:var(--muted);font-weight:600}
.form-submit{width:100%;height:50px;background:linear-gradient(135deg,var(--gold),var(--amber));border:none;color:#120e00;font-family:var(--font-body);font-size:.9rem;font-weight:700;letter-spacing:.3px;border-radius:var(--radius);margin-top:8px;transition:all .25s;box-shadow:0 4px 20px rgba(201,168,76,.3)}
[dir="rtl"] .form-submit{font-family:var(--font-ar)}
.form-submit:hover{transform:translateY(-2px);box-shadow:0 8px 32px rgba(201,168,76,.45)}

.emp-profile-hero{display:flex;gap:22px;align-items:center;margin-bottom:28px;padding-bottom:28px;border-bottom:1px solid var(--border)}
.emp-profile-ava{width:88px;height:88px;border-radius:50%;flex-shrink:0;display:flex;align-items:center;justify-content:center;font-size:2.5rem;border:3px solid;box-shadow:0 0 0 4px rgba(201,168,76,.15)}
.emp-profile-info{flex:1}
.ep-trade{font-size:.7rem;font-weight:700;letter-spacing:2px;text-transform:uppercase;color:var(--gold);margin-bottom:5px}
[dir="rtl"] .ep-trade{letter-spacing:0;text-transform:none}
.ep-name{font-family:var(--font-display);font-size:1.9rem;font-weight:700;letter-spacing:-.3px;line-height:1.1}
[dir="rtl"] .ep-name{font-family:var(--font-ar);font-weight:900;letter-spacing:0}
.ep-stars{display:flex;align-items:center;gap:8px;margin-top:8px}
.ep-rate-block{text-align:right}
[dir="rtl"] .ep-rate-block{text-align:left}
.ep-rate-big{font-family:var(--font-display);font-size:2.2rem;font-weight:700;background:linear-gradient(135deg,var(--gold),var(--amber));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;line-height:1}
[dir="rtl"] .ep-rate-big{font-family:var(--font-ar)}
.ep-rate-unit{font-size:.7rem;color:var(--muted);text-transform:uppercase}
[dir="rtl"] .ep-rate-unit{text-transform:none}
.info-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:22px}
.info-tile{background:var(--input-bg);border:1px solid var(--border);border-radius:var(--radius);padding:14px 16px}
.info-tile-lbl{font-size:.65rem;font-weight:700;letter-spacing:1.5px;text-transform:uppercase;color:var(--muted);margin-bottom:5px}
[dir="rtl"] .info-tile-lbl{letter-spacing:0;text-transform:none}
.info-tile-val{font-size:.9rem;font-weight:600}
.emp-bio-block{background:var(--input-bg);border:1px solid var(--border);border-radius:var(--radius);padding:16px;font-size:.85rem;color:var(--text2);line-height:1.7;margin-bottom:22px}
.review-mini{padding:14px 0;border-bottom:1px solid var(--border)}
.review-mini:last-child{border-bottom:none}
.review-mini-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:5px}
.review-mini-author{font-size:.85rem;font-weight:600}
.review-mini-stars{color:var(--gold);font-size:.8rem}
.review-mini-text{font-size:.8rem;color:var(--muted)}

.toast{position:fixed;bottom:28px;right:28px;z-index:9999;min-width:280px;max-width:360px;background:var(--card);border:1px solid var(--border2);border-left:3px solid var(--gold);border-radius:var(--radius);padding:16px 20px;display:flex;align-items:center;gap:12px;box-shadow:0 8px 32px var(--shadow);transform:translateX(120%);opacity:0;transition:all .4s var(--ease-out)}
[dir="rtl"] .toast{right:auto;left:28px;border-left:none;border-right:3px solid var(--gold);transform:translateX(-120%)}
.toast.show{transform:translateX(0);opacity:1}
.toast.err{border-left-color:var(--rose)}
[dir="rtl"] .toast.err{border-right-color:var(--rose)}
.toast-icon{font-size:1.2rem;flex-shrink:0}
.toast-body{flex:1}
.toast-title{font-size:.85rem;font-weight:600;margin-bottom:2px}
.toast-msg{font-size:.78rem;color:var(--muted)}

@keyframes reveal{from{opacity:0;transform:translateY(22px)}to{opacity:1;transform:translateY(0)}}
.scroll-reveal{opacity:0;transform:translateY(30px);transition:opacity .7s,transform .7s}
.scroll-reveal.visible{opacity:1;transform:translateY(0)}

@media(max-width:1100px){.services-grid{grid-template-columns:repeat(2,1fr)}.how-grid{grid-template-columns:repeat(2,1fr);gap:32px}.how-grid::before{display:none}.reviews-grid{grid-template-columns:repeat(2,1fr)}}
@media(max-width:768px){nav{padding:0 20px}.nav-center{display:none}.nav-hamburger{display:flex}.hero{padding:110px 20px 80px}.hero-deco{display:none}.hero-stats{flex-wrap:wrap}.hero-stat{flex:1 1 40%}.search-section{padding:0 20px 60px}.section{padding:70px 20px}.services-grid{grid-template-columns:1fr}.how-grid{grid-template-columns:1fr 1fr}.reviews-grid{grid-template-columns:1fr}.footer-top{grid-template-columns:1fr 1fr}footer{padding:60px 20px 32px}.modal{padding:32px 20px;margin:10px}.form-grid{grid-template-columns:1fr}.info-grid{grid-template-columns:1fr}.trust-items{flex-wrap:wrap;gap:24px}.trust-item{border:none;flex:1 1 40%}}
@media(max-width:480px){.how-grid{grid-template-columns:1fr}.footer-top{grid-template-columns:1fr}.hero-stat{flex:1 1 100%}}
</style>
</head>
<body>

<div class="ambient">
  <div class="ambient-orb orb1"></div>
  <div class="ambient-orb orb2"></div>
  <div class="ambient-orb orb3"></div>
</div>
<div class="grain"></div>

<nav id="navbar">
  <div class="nav-logo">FixIt<div class="dot"></div></div>
  <div class="nav-center">
    <a href="#services" data-i18n="nav.services">Services</a>
    <a href="#employees" data-i18n="nav.pros">Find a Pro</a>
    <a href="#how" data-i18n="nav.how">How It Works</a>
    <a href="#reviews" data-i18n="nav.reviews">Reviews</a>
  </div>
  <div class="nav-actions">
    <button class="btn-nav-lang" onclick="toggleLang()" id="langBtn">🌐 عربي</button>
    <button class="btn-nav-theme" onclick="toggleTheme()" id="themeBtn">🌙</button>
    <button class="btn-nav-cta" onclick="openRegModal()" data-i18n="nav.register">Join as a Pro</button>
    <button class="nav-hamburger" onclick="toggleMobileMenu()"><span></span><span></span><span></span></button>
  </div>
</nav>

<section class="hero" id="home">
  <div class="hero-bg-lines"></div>
  <div class="hero-deco"><div class="hero-deco-inner"><div class="hero-deco-core">🏠</div></div></div>
  <div class="hero-eyebrow">
    <div class="hero-eyebrow-line"></div>
    <span class="hero-eyebrow-text" data-i18n="hero.badge">Trusted Home Services Platform</span>
  </div>
  <h1 class="hero-title" data-i18n-html="hero.h1">
    <span class="line1">Craft Your</span>
    <span class="line2">Perfect Home.</span>
    <span class="line3">Guaranteed.</span>
  </h1>
  <p class="hero-sub" data-i18n="hero.sub">Connect with certified electricians, plumbers, carpenters, blacksmiths, painters, and construction pros — fast, vetted, and at fair prices.</p>
  <div class="hero-ctas">
    <button class="btn-hero-primary" onclick="smoothScroll('services')" data-i18n="hero.explore">
      Explore Services
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
    </button>
    <button class="btn-hero-secondary" onclick="openBookModal(null,null)" data-i18n="hero.quote">Get a Free Quote</button>
  </div>
  <div class="hero-stats">
    <div class="hero-stat"><div class="hero-stat-val">12K+</div><div class="hero-stat-lbl" data-i18n="hero.stat1">Jobs Done</div></div>
    <div class="hero-stat"><div class="hero-stat-val">500+</div><div class="hero-stat-lbl" data-i18n="hero.stat2">Verified Pros</div></div>
    <div class="hero-stat"><div class="hero-stat-val">4.9★</div><div class="hero-stat-lbl" data-i18n="hero.stat3">Avg Rating</div></div>
    <div class="hero-stat"><div class="hero-stat-val">48h</div><div class="hero-stat-lbl" data-i18n="hero.stat4">Response</div></div>
  </div>
  <div class="hero-scroll"><div class="scroll-line"></div><span data-i18n="hero.scroll">scroll</span></div>
</section>

<div class="search-section">
  <div class="search-wrapper scroll-reveal">
    <span class="search-icon">🔍</span>
    <input class="search-input" type="text" id="searchInput" data-i18n-ph="search.ph" placeholder="What service do you need?"/>
    <div class="search-divider"></div>
    <select class="search-loc" id="locationSel">
      <option data-i18n="loc.any">Any Location</option>
      <option data-i18n="loc.downtown">Downtown</option>
      <option data-i18n="loc.suburbs">Suburbs</option>
      <option data-i18n="loc.north">North District</option>
      <option data-i18n="loc.south">South District</option>
    </select>
    <button class="search-btn" onclick="handleSearch()">
      <span data-i18n="search.btn">Search</span>
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
    </button>
  </div>
</div>

<section class="section" id="services">
  <div class="section-header scroll-reveal">
    <div class="section-kicker"><div class="section-kicker-line"></div><span data-i18n="svc.kicker">What We Offer</span></div>
    <h2 class="section-title" data-i18n="svc.title">Our Six Core Services</h2>
    <p class="section-sub" data-i18n="svc.sub">Every professional is vetted, rated, and ready. Click any service to browse the pros.</p>
  </div>
  <div class="services-grid">
    <div class="svc-card scroll-reveal" data-s="electrician" onclick="filterEmps('electrician');smoothScroll('employees')"><div class="svc-num">01</div><div class="svc-icon-wrap">⚡</div><div class="svc-name" data-i18n="svc.electrician">Electrician</div><p class="svc-desc" data-i18n="svc.electrician.d">Wiring, circuit breakers, panel upgrades, smart home systems, and full electrical inspections.</p><div class="svc-footer"><div class="svc-price" data-i18n="svc.electrician.p">From $80 / hr</div><div class="svc-arrow">→</div></div></div>
    <div class="svc-card scroll-reveal" data-s="plumber" style="animation-delay:.05s" onclick="filterEmps('plumber');smoothScroll('employees')"><div class="svc-num">02</div><div class="svc-icon-wrap">🔧</div><div class="svc-name" data-i18n="svc.plumber">Plumber</div><p class="svc-desc" data-i18n="svc.plumber.d">Pipe repairs, drain cleaning, water heaters, leak detection, and complete plumbing overhauls.</p><div class="svc-footer"><div class="svc-price" data-i18n="svc.plumber.p">From $75 / hr</div><div class="svc-arrow">→</div></div></div>
    <div class="svc-card scroll-reveal" data-s="carpenter" style="animation-delay:.1s" onclick="filterEmps('carpenter');smoothScroll('employees')"><div class="svc-num">03</div><div class="svc-icon-wrap">🪵</div><div class="svc-name" data-i18n="svc.carpenter">Carpenter</div><p class="svc-desc" data-i18n="svc.carpenter.d">Custom furniture, cabinetry, door framing, deck construction, and fine woodworking.</p><div class="svc-footer"><div class="svc-price" data-i18n="svc.carpenter.p">From $65 / hr</div><div class="svc-arrow">→</div></div></div>
    <div class="svc-card scroll-reveal" data-s="blacksmith" style="animation-delay:.15s" onclick="filterEmps('blacksmith');smoothScroll('employees')"><div class="svc-num">04</div><div class="svc-icon-wrap">🔩</div><div class="svc-name" data-i18n="svc.blacksmith">Blacksmith</div><p class="svc-desc" data-i18n="svc.blacksmith.d">Custom ironwork, decorative gates, railings, hinges, brackets, and ornamental metalwork.</p><div class="svc-footer"><div class="svc-price" data-i18n="svc.blacksmith.p">From $90 / hr</div><div class="svc-arrow">→</div></div></div>
    <div class="svc-card scroll-reveal" data-s="painter" style="animation-delay:.2s" onclick="filterEmps('painter');smoothScroll('employees')"><div class="svc-num">05</div><div class="svc-icon-wrap">🎨</div><div class="svc-name" data-i18n="svc.painter">Painter</div><p class="svc-desc" data-i18n="svc.painter.d">Interior and exterior painting, wallpaper removal, texture finishes, and color consultation.</p><div class="svc-footer"><div class="svc-price" data-i18n="svc.painter.p">From $55 / hr</div><div class="svc-arrow">→</div></div></div>
    <div class="svc-card scroll-reveal" data-s="construction" style="animation-delay:.25s" onclick="filterEmps('construction');smoothScroll('employees')"><div class="svc-num">06</div><div class="svc-icon-wrap">🧱</div><div class="svc-name" data-i18n="svc.construction">Walls & Ceilings</div><p class="svc-desc" data-i18n="svc.construction.d">Plastering, drywall, tiling, partition walls, false ceilings, and full renovation works.</p><div class="svc-footer"><div class="svc-price" data-i18n="svc.construction.p">From $70 / hr</div><div class="svc-arrow">→</div></div></div>
  </div>
</section>

<div class="trust-banner scroll-reveal">
  <div class="trust-items">
    <div class="trust-item"><div class="trust-icon">🛡️</div><div class="trust-label" data-i18n="trust.1">All Pros Vetted & Insured</div></div>
    <div class="trust-item"><div class="trust-icon">⚡</div><div class="trust-label" data-i18n="trust.2">Same-Day Availability</div></div>
    <div class="trust-item"><div class="trust-icon">💳</div><div class="trust-label" data-i18n="trust.3">Secure Payments</div></div>
    <div class="trust-item"><div class="trust-icon">🔄</div><div class="trust-label" data-i18n="trust.4">Satisfaction Guarantee</div></div>
    <div class="trust-item"><div class="trust-icon">⭐</div><div class="trust-label" data-i18n="trust.5">Verified Reviews Only</div></div>
  </div>
</div>

<section class="section emp-section" id="employees">
  <div class="section-header scroll-reveal">
    <div class="section-kicker"><div class="section-kicker-line"></div><span data-i18n="emp.kicker">Browse Professionals</span></div>
    <h2 class="section-title" data-i18n="emp.title">Find Your Perfect Pro</h2>
    <p class="section-sub" data-i18n="emp.sub">Each pro sets their own price. Browse ratings, read bios, and hire the one that fits.</p>
  </div>
  <div class="filter-bar scroll-reveal" id="filterBar">
    <button class="filter-pill active" data-f="all" onclick="filterEmps('all')" data-i18n="filter.all">All Trades</button>
    <button class="filter-pill" data-f="electrician" onclick="filterEmps('electrician')" data-i18n="svc.electrician">Electrician</button>
    <button class="filter-pill" data-f="plumber" onclick="filterEmps('plumber')" data-i18n="svc.plumber">Plumber</button>
    <button class="filter-pill" data-f="carpenter" onclick="filterEmps('carpenter')" data-i18n="svc.carpenter">Carpenter</button>
    <button class="filter-pill" data-f="blacksmith" onclick="filterEmps('blacksmith')" data-i18n="svc.blacksmith">Blacksmith</button>
    <button class="filter-pill" data-f="painter" onclick="filterEmps('painter')" data-i18n="svc.painter">Painter</button>
    <button class="filter-pill" data-f="construction" onclick="filterEmps('construction')" data-i18n="svc.construction">Walls & Ceilings</button>
  </div>
  <div class="emp-grid" id="empGrid"></div>
</section>

<section class="section" id="how" style="background:var(--bg2);border-top:1px solid var(--border)">
  <div class="section-header scroll-reveal" style="text-align:center;max-width:600px;margin:0 auto 60px">
    <div class="section-kicker" style="justify-content:center"><div class="section-kicker-line"></div><span data-i18n="how.kicker">Simple Process</span><div class="section-kicker-line"></div></div>
    <h2 class="section-title" data-i18n="how.title">How It Works</h2>
    <p class="section-sub" style="margin:0 auto" data-i18n="how.sub">From search to service in four simple steps.</p>
  </div>
  <div class="how-grid scroll-reveal">
    <div class="how-step"><div class="how-step-icon-wrap">🔍</div><div class="how-step-title" data-i18n="how.s1.t">Choose a Service</div><p class="how-step-desc" data-i18n="how.s1.d">Browse our six core trades and find exactly what your home needs.</p></div>
    <div class="how-step"><div class="how-step-icon-wrap">👤</div><div class="how-step-title" data-i18n="how.s2.t">Pick a Pro</div><p class="how-step-desc" data-i18n="how.s2.d">Compare ratings, bios, and hourly rates — then choose the best fit.</p></div>
    <div class="how-step"><div class="how-step-icon-wrap">📋</div><div class="how-step-title" data-i18n="how.s3.t">Book Instantly</div><p class="how-step-desc" data-i18n="how.s3.d">Submit your request in under two minutes. The pro confirms your slot.</p></div>
    <div class="how-step"><div class="how-step-icon-wrap">✅</div><div class="how-step-title" data-i18n="how.s4.t">Job Done</div><p class="how-step-desc" data-i18n="how.s4.d">Work completed to your satisfaction. Pay securely and leave a review.</p></div>
  </div>
</section>

<section class="section reviews-section" id="reviews">
  <div class="section-header scroll-reveal">
    <div class="section-kicker"><div class="section-kicker-line"></div><span data-i18n="rev.kicker">Client Voices</span></div>
    <h2 class="section-title" data-i18n="rev.title">What Our Clients Say</h2>
  </div>
  <div class="reviews-grid">
    <div class="review-card scroll-reveal"><div class="review-stars-row"><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span></div><p class="review-text" data-i18n="rev.1">"The electrician arrived on time, diagnosed the issue in minutes, and had everything fixed within two hours. Clean, professional, outstanding."</p><div class="review-author-row"><div class="review-author-avatar">👨</div><div><div class="review-author-name">Marcus T.</div><div class="review-author-role" data-i18n="rev.1r">Homeowner · Electrician</div></div></div></div>
    <div class="review-card scroll-reveal" style="animation-delay:.05s"><div class="review-stars-row"><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span></div><p class="review-text" data-i18n="rev.2">"Same-day plumber service, no hidden costs. He found the leak we couldn't see and fixed the whole line. Highly recommended."</p><div class="review-author-row"><div class="review-author-avatar">👩</div><div><div class="review-author-name">Priya N.</div><div class="review-author-role" data-i18n="rev.2r">Apartment Owner · Plumber</div></div></div></div>
    <div class="review-card scroll-reveal" style="animation-delay:.1s"><div class="review-stars-row"><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span><span class="review-star" style="opacity:.3">★</span></div><p class="review-text" data-i18n="rev.3">"Beautiful built-in shelving — crafted perfectly to our space. The carpenter was meticulous and the finish is stunning."</p><div class="review-author-row"><div class="review-author-avatar">👫</div><div><div class="review-author-name">James & Carol R.</div><div class="review-author-role" data-i18n="rev.3r">Property Owners · Carpenter</div></div></div></div>
    <div class="review-card scroll-reveal" style="animation-delay:.15s"><div class="review-stars-row"><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span></div><p class="review-text" data-i18n="rev.4">"The walls and ceiling renovation exceeded every expectation. On-time, immaculate finish — I've already booked them again."</p><div class="review-author-row"><div class="review-author-avatar">👩‍💼</div><div><div class="review-author-name">Sofia M.</div><div class="review-author-role" data-i18n="rev.4r">Villa Owner · Construction</div></div></div></div>
    <div class="review-card scroll-reveal" style="animation-delay:.2s"><div class="review-stars-row"><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span></div><p class="review-text" data-i18n="rev.5">"Whole-house repaint in three days — zero mess, perfect prep. The colour consultant's suggestions transformed the space."</p><div class="review-author-row"><div class="review-author-avatar">👨</div><div><div class="review-author-name">Derrick B.</div><div class="review-author-role" data-i18n="rev.5r">Homeowner · Painter</div></div></div></div>
    <div class="review-card scroll-reveal" style="animation-delay:.25s"><div class="review-stars-row"><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span><span class="review-star">★</span><span class="review-star" style="opacity:.3">★</span></div><p class="review-text" data-i18n="rev.6">"Seamless booking, transparent pricing, and a pro who genuinely cared about the result. This is my go-to platform now."</p><div class="review-author-row"><div class="review-author-avatar">👩‍🦱</div><div><div class="review-author-name">Angela W.</div><div class="review-author-role" data-i18n="rev.6r">Repeat Client · Multiple</div></div></div></div>
  </div>
</section>

<footer id="contact">
  <div class="footer-top">
    <div>
      <div class="footer-brand">FixIt</div>
      <p class="footer-tagline" data-i18n="footer.tag">Connecting homeowners with elite tradespeople since 2019. Quality guaranteed on every job.</p>
      <div class="footer-social">
        <a class="social-btn" href="#">𝕏</a>
        <a class="social-btn" href="#">📷</a>
        <a class="social-btn" href="#">f</a>
        <a class="social-btn" href="#">in</a>
      </div>
    </div>
    <div>
      <div class="footer-col-title" data-i18n="footer.services">Services</div>
      <ul class="footer-links">
        <li><a onclick="filterEmps('electrician');smoothScroll('employees')" data-i18n="svc.electrician">Electrician</a></li>
        <li><a onclick="filterEmps('plumber');smoothScroll('employees')" data-i18n="svc.plumber">Plumber</a></li>
        <li><a onclick="filterEmps('carpenter');smoothScroll('employees')" data-i18n="svc.carpenter">Carpenter</a></li>
        <li><a onclick="filterEmps('blacksmith');smoothScroll('employees')" data-i18n="svc.blacksmith">Blacksmith</a></li>
        <li><a onclick="filterEmps('painter');smoothScroll('employees')" data-i18n="svc.painter">Painter</a></li>
        <li><a onclick="filterEmps('construction');smoothScroll('employees')" data-i18n="svc.construction">Walls & Ceilings</a></li>
      </ul>
    </div>
    <div>
      <div class="footer-col-title" data-i18n="footer.company">Company</div>
      <ul class="footer-links">
        <li><a href="#" data-i18n="footer.about">About Us</a></li>
        <li><a href="#" data-i18n="footer.careers">Careers</a></li>
        <li><button onclick="openRegModal()" data-i18n="footer.join">Join as a Pro</button></li>
        <li><a href="#" data-i18n="footer.press">Press</a></li>
        <li><a href="#" data-i18n="footer.blog">Blog</a></li>
      </ul>
    </div>
    <div>
      <div class="footer-col-title" data-i18n="footer.support">Support</div>
      <ul class="footer-links">
        <li><a href="#" data-i18n="footer.help">Help Center</a></li>
# mo
