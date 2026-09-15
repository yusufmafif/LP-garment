<script lang="ts">
  import { onMount } from 'svelte';

  let scrolled = false;

  onMount(() => {
    const onScroll = () => { scrolled = window.scrollY > 50; };
    window.addEventListener('scroll', onScroll, { passive: true });

    const revealEls = document.querySelectorAll('.reveal');
    const io = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) { e.target.classList.add('visible'); io.unobserve(e.target); }
      });
    }, { threshold: 0.1, rootMargin: '0px 0px -48px 0px' });
    revealEls.forEach(el => io.observe(el));

    return () => { window.removeEventListener('scroll', onScroll); io.disconnect(); };
  });

  const WA_BASE = 'https://wa.me/628981299833';
  const wa = (text: string) => `${WA_BASE}?text=${encodeURIComponent(text)}`;
</script>

<svelte:head>
  <title>Jasa Web Tasik — Website untuk Reseller & Grosir Busana Muslim</title>
  
  <!-- Open Graph / Facebook / WhatsApp -->
  <meta property="og:type" content="website" />
  <meta property="og:url" content="https://webgarment.vercel.app/" />
  <meta property="og:title" content="Jasa Web Tasik — Website untuk Reseller & Grosir Busana Muslim" />
  <meta property="og:description" content="Jasa pembuatan website profesional untuk reseller dan grosir busana muslim di Tasikmalaya. Katalog online, koneksi WhatsApp, harga transparan." />
  <meta property="og:image" content="https://webgarment.vercel.app/preview.webp" />

  <!-- Twitter -->
  <meta name="twitter:card" content="summary_large_image" />
  <meta name="twitter:url" content="https://webgarment.vercel.app/" />
  <meta name="twitter:title" content="Jasa Web Tasik — Website untuk Reseller & Grosir Busana Muslim" />
  <meta name="twitter:description" content="Jasa pembuatan website profesional untuk reseller dan grosir busana muslim di Tasikmalaya. Katalog online, koneksi WhatsApp, harga transparan." />
  <meta name="twitter:image" content="https://webgarment.vercel.app/preview.webp" />
</svelte:head>

<!-- ── NAV ─────────────────────────────────────── -->
<nav class:scrolled>
  <div class="container nav-inner">
    <div class="nav-logo">Jasa Web <span>Tasik.</span></div>
    <a href={wa('Halo, saya mau konsultasi soal website')} class="nav-cta" target="_blank" rel="noopener">
      Chat WhatsApp
    </a>
  </div>
</nav>

<!-- ── HERO ─────────────────────────────────────── -->
<section class="hero">
  <div class="container hero-inner">

    <div class="hero-text">
      <p class="hero-tag">Tasikmalaya · Jawa Barat</p>
      <h1 class="hero-headline">
        Website<br>Profesional<br>untuk Reseller<br><span class="hl">&amp; Grosir<br>Busana Muslim</span>
      </h1>
      <p class="hero-sub">
        Biar katalog produk kamu nggak ilang dalam 24 jam kayak story WA — tampil rapi, gampang di-share, siap terima orderan kapan aja.
      </p>
      <div class="hero-actions">
        <a href={wa('Halo, saya mau konsultasi gratis soal website untuk bisnis saya')} class="btn-green" target="_blank" rel="noopener">
          <svg viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
          Konsultasi Gratis via WhatsApp
        </a>
      </div>
    </div>

    <!-- Visual block — 3 overlapping photos -->
    <div class="hero-visual">
      <div class="hero-stack" aria-hidden="true">
        <img src="/3.webp" class="stack-img img-back-left" alt="" />
        <img src="/2.webp" class="stack-img img-back-right" alt="" />
        <img src="/1.webp" class="stack-img img-front" alt="" />
        <!-- floating label -->
        <div class="hero-float-tag">Katalog Online · Selalu Ada</div>
      </div>
    </div>

  </div>

  <!-- bottom marquee strip -->
  <div class="hero-strip">
    <div class="strip-track">
      {#each Array(12) as _}
        <span>Katalog Online</span><span class="strip-dot">·</span>
        <span>Koneksi WA</span><span class="strip-dot">·</span>
        <span>Harga Transparan</span><span class="strip-dot">·</span>
        <span>Siap Orderan</span><span class="strip-dot">·</span>
      {/each}
    </div>
  </div>
</section>

<!-- ── PORTFOLIO ──────────────────────────────── -->
<section class="section" id="portfolio">
  <div class="container">
    <div class="pf-header reveal">
      <div>
        <p class="eyebrow">Portofolio Kami</p>
        <h2 class="h2">Sudah Dipercaya<br>Bisnis Lokal</h2>
      </div>
      <p class="pf-header-sub">Setiap website dibuat sesuai karakter bisnisnya — bukan copy-paste template yang sama rata.</p>
    </div>

    <div class="pf-grid">
      <!-- Featured card -->
      <article class="pf-card pf-card--lg reveal">
        <div class="pf-img pf-img--dark">
          <div class="pf-browser-mock">
            <div class="pbm-bar"><span></span><span></span><span></span><div class="pbm-url"></div></div>
            <div class="pbm-content" style="padding: 0;">
              <img src="/1.webp" alt="Vitalpria Preview" style="width: 100%; height: 100%; object-fit: cover; border-radius: 0 0 6px 6px; display: block;" />
            </div>
          </div>
        </div>
        <div class="pf-info">
          <div class="pf-info-left">
            <h3 class="pf-name">Update promo-promo tokomu</h3>
            <p class="pf-caption">Banner Slide</p>
          </div>
          <a href="https://khalisa-wear.vercel.app/" class="pf-link" target="_blank" rel="noopener" aria-label="Lihat Vitalpria">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M7 17L17 7M17 7H7M17 7v10"/></svg>
          </a>
        </div>
      </article>

      <!-- Card 2 -->
      <article class="pf-card reveal" style="transition-delay:0.08s">
        <div class="pf-img pf-img--light">
          <div class="pf-browser-mock">
            <div class="pbm-bar"><span></span><span></span><span></span><div class="pbm-url"></div></div>
            <div class="pbm-content" style="padding: 0;">
              <img src="/3.webp" alt="Toko Hijab Rani Preview" style="width: 100%; height: 100%; object-fit: cover; border-radius: 0 0 6px 6px; display: block;" />
            </div>
          </div>
        </div>
        <div class="pf-info">
          <div class="pf-info-left">
            <h3 class="pf-name">Halaman daftar produkmu</h3>
            <p class="pf-caption">Katalog produk lengkap</p>
          </div>
        </div>
      </article>

      <!-- Card 3 -->
      <article class="pf-card reveal" style="transition-delay:0.16s">
        <div class="pf-img pf-img--green">
          <div class="pf-browser-mock">
            <div class="pbm-bar"><span></span><span></span><span></span><div class="pbm-url"></div></div>
            <div class="pbm-content" style="padding: 0;">
              <img src="/4.webp" alt="Grosir Busana Nida Preview" style="width: 100%; height: 100%; object-fit: cover; border-radius: 0 0 6px 6px; display: block;" />
            </div>
          </div>
        </div>
        <div class="pf-info">
          <div class="pf-info-left">
            <h3 class="pf-name">Halaman detail dan CTA</h3>
            <p class="pf-caption">Detail Produkmua dan variannya</p>
          </div>
        </div>
      </article>
    </div>
  </div>
</section>

<!-- ── WHY ────────────────────────────────────── -->
<section class="section why-section" id="kenapa">
  <div class="container">
    <div class="why-top reveal">
      <p class="eyebrow">Kenapa Pilih Kami</p>
      <h2 class="h2">Dibuat untuk cara jualan<br>kamu yang sebenarnya</h2>
    </div>

    <div class="why-grid">
      {#each [
        { n:'01', title:'Paham Kebutuhan Reseller Lokal',   body:'Bukan template generik — saya bikin website yang ngerti cara reseller/grosir busana muslim jualan sehari-hari.' },
        { n:'02', title:'Cepat & Jelas Harganya',           body:'Nggak perlu nunggu berminggu-minggu, harga transparan dari awal, nggak ada biaya tersembunyi.' },
        { n:'03', title:'Terhubung Langsung ke WhatsApp',   body:'Customer bisa lihat katalog, lalu langsung chat kamu buat closing — nggak ribet pindah-pindah platform.' },
        { n:'04', title:'Tersedia Opsi Self-Update',        body:'Mau update produk/harga sendiri kapan aja tanpa nunggu saya? Ada paket dengan dashboard CMS.' },
      ] as item, i}
        <div class="why-card reveal" style="transition-delay:{i * 0.07}s">
          <span class="why-n">{item.n}</span>
          <h3 class="why-title">{item.title}</h3>
          <p class="why-body">{item.body}</p>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- ── PRICING ────────────────────────────────── -->
<section class="section pricing-section" id="harga">
  <div class="container">
    <div class="pricing-grid">

      <div class="pricing-left reveal">
        <p class="eyebrow">Investasi yang Sepadan</p>
        <h2 class="h2">Harga sesuai,<br>tanpa kaget<br>di tengah jalan</h2>
        <p class="pricing-body">Website yang kamu bayar adalah website yang kamu dapat — tidak ada biaya kejutan di tengah proses atau setelah selesai.</p>
        <ul class="pricing-list">
          {#each ['Desain sesuai karakter bisnis kamu','Tampilan katalog produk yang rapi','Tombol WA langsung ke nomermu','Mobile-friendly & cepat dibuka','Opsi CMS untuk update mandiri (paket tertentu)'] as item}
            <li><span class="li-dot"></span>{item}</li>
          {/each}
        </ul>
      </div>

      <div class="pricing-card reveal">
        <div class="pc-tag">Harga Transparan</div>
        <div class="pc-amount">Rp 500rb</div>
        <p class="pc-note">harga mulai dari — final sesuai kebutuhan kamu</p>
        <div class="pc-divider"></div>
        <p class="pc-desc">Paket website mulai dari Rp 500.000 — sudah termasuk desain, tampilan produk, dan koneksi ke WhatsApp. Harga final tergantung kebutuhan (jumlah halaman, fitur CMS, dll).</p>
        <a href={wa('Halo, saya mau tanya detail harga website')} class="btn-green-outline" target="_blank" rel="noopener">
          Tanya Detail Harga
        </a>
      </div>

    </div>
  </div>
</section>

<!-- ── CTA ────────────────────────────────────── -->
<section class="cta-section">
  <div class="container cta-inner">
    <p class="eyebrow cta-eyebrow">Mulai Sekarang</p>
    <h2 class="h2 cta-h2">Siap Punya<br>Website Sendiri?</h2>
    <a href={wa('Halo, saya mau mulai bikin website untuk bisnis saya')} class="btn-green btn-green--lg" target="_blank" rel="noopener">
      <svg viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
      Chat Saya Sekarang
    </a>
  </div>
</section>

<!-- ── FOOTER ─────────────────────────────────── -->
<footer>
  <div class="container footer-inner">
    <div class="footer-logo">Jasa Web <span>Tasik.</span></div>
    <p class="footer-copy">Jasa pembuatan website untuk reseller & grosir busana muslim · Tasikmalaya</p>
  </div>
</footer>

<style>
  /* ── Tokens ──────────────────────────────────── */
  :global(*), :global(*::before), :global(*::after) { box-sizing: border-box; margin: 0; padding: 0; }
  :global(:root) {
    --white:   #FFFFFF;
    --off:     #F6F5F2;
    --dark:    #1E2019;
    --dark-2:  #2A2B24;
    --green:   #7AB318;
    --green-d: #5E8A10;
    --green-l: #EEF5E0;
    --text:    #1A1A18;
    --muted:   #7A7A72;
    --border:  #E4E4DC;
    --serif:   'Plus Jakarta Sans', system-ui, sans-serif;
    --sans:    'Plus Jakarta Sans', system-ui, sans-serif;
    --s--1: clamp(0.78rem, 0.74rem + 0.22vw, 0.88rem);
    --s-0:  clamp(1rem,    0.96rem + 0.28vw, 1.06rem);
    --s-1:  clamp(1.18rem, 1.08rem + 0.56vw, 1.45rem);
    --s-2:  clamp(1.5rem,  1.2rem  + 1.5vw,  2.2rem);
    --s-3:  clamp(2rem,    1.5rem  + 2.5vw,  3.4rem);
    --s-4:  clamp(2.8rem,  1.8rem  + 4.5vw,  5.2rem);
  }
  :global(html) { scroll-behavior: smooth; }
  :global(body) { font-family: var(--sans); font-size: var(--s-0); color: var(--text); background: var(--white); line-height: 1.6; -webkit-font-smoothing: antialiased; }
  :global(a) { color: inherit; text-decoration: none; }
  :global(img) { display: block; max-width: 100%; }

  .container { width: min(1160px, 100% - 3rem); margin-inline: auto; }

  /* ── NAV ──────────────────────────────────────── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    padding: 1.1rem 0;
    background: rgba(255,255,255,0.94);
    backdrop-filter: blur(12px);
    box-shadow: 0 1px 0 var(--border);
    transition: padding 0.25s, box-shadow 0.25s;
  }
  nav.scrolled { padding: 0.9rem 0; box-shadow: 0 4px 20px rgba(0,0,0,0.05); }
  .nav-inner { display: flex; align-items: center; justify-content: space-between; }
  .nav-logo { font-size: var(--s-1); font-weight: 800; color: var(--dark); letter-spacing: -0.03em; line-height: 1; }
  .nav-logo span { color: var(--green); }
  .nav-cta {
    font-size: var(--s--1); font-weight: 700; letter-spacing: -0.01em;
    color: var(--white); background: var(--dark);
    padding: 0.55rem 1.15rem; border-radius: 100px;
    transition: background 0.2s;
  }
  .nav-cta:hover { background: var(--green); }

  /* ── HERO ──────────────────────────────────────── */
  .hero {
    min-height: 100dvh; background: var(--white);
    display: flex; flex-direction: column; justify-content: space-between;
    padding-top: clamp(5.5rem, 10vw, 8rem);
    overflow: hidden;
  }
  .hero-inner {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 3rem; align-items: center;
    flex: 1; padding-bottom: 3rem;
  }
  .hero-tag {
    font-size: var(--s--1); font-weight: 600; color: var(--muted);
    letter-spacing: 0.06em; text-transform: uppercase;
    margin-bottom: 1.2rem;
  }
  .hero-headline {
    font-size: var(--s-4); font-weight: 800; line-height: 1.04;
    letter-spacing: -0.04em; color: var(--dark); margin-bottom: 1.5rem;
  }
  .hero-headline .hl { color: var(--green); }
  .hero-sub { font-size: var(--s-0); color: var(--muted); max-width: 46ch; line-height: 1.7; margin-bottom: 2.2rem; }
  .hero-actions { display: flex; gap: 1rem; flex-wrap: wrap; align-items: center; }

  /* Stacked visual */
  .hero-visual { position: relative; display: flex; justify-content: flex-end; }
  .hero-stack {
    position: relative;
    width: 100%;
    max-width: 500px;
    aspect-ratio: 1; /* roughly square container */
    margin-right: 2rem;
  }
  .stack-img {
    position: absolute;
    border-radius: 12px;
    box-shadow: 0 12px 32px rgba(0,0,0,0.12);
    object-fit: cover;
    transition: transform 0.3s ease;
  }
  .img-back-left {
    width: 55%;
    aspect-ratio: 3/4;
    top: 5%;
    left: 0;
    z-index: 1;
    transform: rotate(-6deg);
  }
  .img-back-right {
    width: 55%;
    aspect-ratio: 4/5;
    top: 0;
    right: 0;
    z-index: 2;
    transform: rotate(8deg);
  }
  .img-front {
    width: 60%;
    aspect-ratio: 3/4;
    bottom: 5%;
    left: 20%;
    z-index: 3;
    border: 6px solid var(--white);
    transform: rotate(-2deg);
  }
  .hero-stack:hover .img-back-left { transform: rotate(-8deg) translate(-10px, -10px); }
  .hero-stack:hover .img-back-right { transform: rotate(10deg) translate(10px, -10px); }
  .hero-stack:hover .img-front { transform: translateY(-5px) rotate(-1deg); }
  .hero-float-tag {
    position: absolute; bottom: 0; left: 10%; z-index: 4;
    background: var(--green); color: var(--white);
    font-size: var(--s--1); font-weight: 700; letter-spacing: -0.01em;
    padding: 0.5rem 1rem; border-radius: 100px;
    white-space: nowrap;
    box-shadow: 0 8px 24px rgba(122,179,24,0.3);
  }

  /* Marquee strip */
  .hero-strip { overflow: hidden; border-top: 1.5px solid var(--border); border-bottom: 1.5px solid var(--border); padding: 0.65rem 0; }
  .strip-track {
    display: flex; gap: 1.2rem; white-space: nowrap;
    animation: marquee 28s linear infinite;
    font-size: var(--s--1); font-weight: 600; color: var(--muted); letter-spacing: 0.02em;
  }
  .strip-dot { color: var(--green); }
  @keyframes marquee { from { transform: translateX(0); } to { transform: translateX(-50%); } }

  /* ── BUTTONS ───────────────────────────────────── */
  .btn-green {
    display: inline-flex; align-items: center; gap: 0.55rem;
    font-weight: 700; font-size: var(--s-0); letter-spacing: -0.01em;
    color: var(--white); background: var(--green);
    padding: 0.75rem 1.5rem; border-radius: 100px;
    transition: background 0.2s, transform 0.15s;
  }
  .btn-green:hover { background: var(--green-d); transform: translateY(-1px); }
  .btn-green svg { width: 17px; height: 17px; flex-shrink: 0; }
  .btn-green--lg { font-size: var(--s-1); padding: 0.9rem 2rem; }
  .btn-green--lg svg { width: 20px; height: 20px; }

  .btn-green-outline {
    display: inline-flex; align-items: center; gap: 0.5rem;
    font-weight: 700; font-size: var(--s--1); letter-spacing: -0.01em;
    color: var(--green); border: 2px solid var(--green);
    padding: 0.65rem 1.35rem; border-radius: 100px;
    transition: background 0.2s, color 0.2s;
  }
  .btn-green-outline:hover { background: var(--green); color: var(--white); }

  /* ── SECTION BASE ─────────────────────────────── */
  .section { padding-block: clamp(4rem, 8vw, 7rem); }
  .eyebrow { font-size: var(--s--1); font-weight: 700; letter-spacing: 0.07em; text-transform: uppercase; color: var(--green); margin-bottom: 0.5rem; }
  .h2 { font-size: var(--s-3); font-weight: 800; line-height: 1.1; letter-spacing: -0.04em; color: var(--dark); }

  /* ── PORTFOLIO ─────────────────────────────────── */
  .pf-header { display: flex; align-items: flex-end; justify-content: space-between; gap: 2rem; margin-bottom: 2.5rem; flex-wrap: wrap; }
  .pf-header-sub { max-width: 36ch; font-size: var(--s--1); color: var(--muted); line-height: 1.65; }
  .pf-grid { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 1.25rem; }
  .pf-card { background: var(--white); border: 1.5px solid var(--border); border-radius: 12px; overflow: hidden; transition: transform 0.25s, box-shadow 0.25s; }
  .pf-card:hover { transform: translateY(-4px); box-shadow: 0 12px 40px rgba(0,0,0,0.08); }
  .pf-card--lg { grid-column: span 1; }

  .pf-img { aspect-ratio: 4/3; display: flex; flex-direction: column; overflow: hidden; padding: 14px 14px 0; }
  .pf-img--dark { background: var(--dark-2); }
  .pf-img--light { background: var(--off); }
  .pf-img--green { background: var(--green-l); }

  /* mini browser inside portfolio card */
  .pf-browser-mock { background: var(--white); border-radius: 6px 6px 0 0; overflow: hidden; flex: 1; display: flex; flex-direction: column; box-shadow: 0 2px 12px rgba(0,0,0,0.12); }
  .pbm-bar { display: flex; align-items: center; gap: 4px; padding: 6px 8px; background: #f0f0ec; border-bottom: 1px solid #e0e0d8; flex-shrink: 0; }
  .pbm-bar span { width: 6px; height: 6px; border-radius: 50%; flex-shrink: 0; }
  .pbm-bar span:nth-child(1) { background:#ff5f57; }
  .pbm-bar span:nth-child(2) { background:#ffbd2e; }
  .pbm-bar span:nth-child(3) { background:#28c840; }
  .pbm-url { flex: 1; height: 12px; background: #e0e0d8; border-radius: 2px; margin: 0 6px; }
  .pbm-content { flex: 1; padding: 8px; display: flex; flex-direction: column; gap: 6px; overflow: hidden; }
  .pbm-hero { border-radius: 4px; background: var(--dark); padding: 10px; display: flex; flex-direction: column; gap: 4px; flex-shrink: 0; }
  .pbm-hl { height: 7px; border-radius: 2px; background: rgba(255,255,255,0.7); }
  .pbm-hl.thin { height: 5px; background: rgba(255,255,255,0.4); }
  .pbm-btn-mock { width: 48px; height: 15px; background: var(--green); border-radius: 100px; margin-top: 4px; }
  .pbm-grid { display: grid; gap: 5px; }
  .pbm-grid:not(.g2) { grid-template-columns: repeat(3,1fr); }
  .pbm-grid.g2 { grid-template-columns: repeat(2,1fr); }
  .pbm-item { aspect-ratio: 3/4; background: #c8c8c0; border-radius: 3px; }
  .pbm-form-mock { display: flex; flex-direction: column; gap: 5px; flex: 1; }
  .pbm-field { height: 16px; background: #f0f0ec; border-radius: 3px; border: 1px solid #ddd; }
  .pbm-submit { height: 18px; background: var(--green); border-radius: 3px; width: 60%; }

  .pf-info { display: flex; align-items: center; justify-content: space-between; padding: 0.9rem 1rem; border-top: 1.5px solid var(--border); gap: 0.75rem; }
  .pf-name { font-size: var(--s-0); font-weight: 700; letter-spacing: -0.02em; color: var(--dark); margin-bottom: 0.2rem; }
  .pf-caption { font-size: var(--s--1); color: var(--muted); line-height: 1.4; }
  .pf-link {
    width: 36px; height: 36px; border-radius: 50%; border: 1.5px solid var(--border);
    display: flex; align-items: center; justify-content: center; flex-shrink: 0;
    transition: background 0.2s, border-color 0.2s;
  }
  .pf-link:hover { background: var(--green); border-color: var(--green); color: var(--white); }
  .pf-link svg { width: 14px; height: 14px; }

  /* ── WHY ───────────────────────────────────────── */
  .why-section { background: var(--dark); }
  .why-section .eyebrow { color: var(--green); }
  .why-section .h2 { color: var(--white); }
  .why-top { margin-bottom: 3rem; }
  .why-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 1.25rem; }
  .why-card {
    background: rgba(255,255,255,0.04); border: 1px solid rgba(255,255,255,0.08);
    border-radius: 12px; padding: 1.75rem 1.5rem;
    display: flex; flex-direction: column; gap: 0.75rem;
    transition: background 0.2s, border-color 0.2s;
  }
  .why-card:hover { background: rgba(122,179,24,0.08); border-color: rgba(122,179,24,0.3); }
  .why-n { font-size: var(--s--1); font-weight: 700; color: var(--green); letter-spacing: 0.05em; }
  .why-title { font-size: var(--s-0); font-weight: 700; color: var(--white); line-height: 1.3; letter-spacing: -0.02em; }
  .why-body { font-size: var(--s--1); color: rgba(255,255,255,0.55); line-height: 1.65; }

  /* ── PRICING ───────────────────────────────────── */
  .pricing-grid { display: grid; grid-template-columns: 1fr 1fr; gap: clamp(2.5rem,5vw,5rem); align-items: center; }
  .pricing-body { font-size: var(--s-0); color: var(--muted); line-height: 1.7; margin-top: 1.25rem; margin-bottom: 0.5rem; }
  .pricing-list { list-style: none; display: flex; flex-direction: column; gap: 0.6rem; margin-top: 1.5rem; }
  .pricing-list li { display: flex; align-items: flex-start; gap: 0.65rem; font-size: var(--s--1); color: var(--text); }
  .li-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--green); flex-shrink: 0; margin-top: 0.5em; }

  .pricing-card {
    background: var(--dark); border-radius: 16px;
    padding: clamp(1.75rem, 4vw, 2.75rem);
  }
  .pc-tag { display: inline-block; font-size: var(--s--1); font-weight: 700; color: var(--green); border: 1.5px solid rgba(122,179,24,0.4); padding: 0.3rem 0.8rem; border-radius: 100px; margin-bottom: 1.5rem; }
  .pc-amount { font-size: clamp(2.4rem, 5vw, 3.6rem); font-weight: 800; color: var(--white); line-height: 1; letter-spacing: -0.04em; margin-bottom: 0.35rem; }
  .pc-note { font-size: var(--s--1); color: rgba(255,255,255,0.45); margin-bottom: 1.5rem; }
  .pc-divider { height: 1px; background: rgba(255,255,255,0.1); margin-bottom: 1.25rem; }
  .pc-desc { font-size: var(--s--1); color: rgba(255,255,255,0.6); line-height: 1.65; margin-bottom: 1.75rem; }

  /* ── CTA ───────────────────────────────────────── */
  .cta-section { background: var(--off); border-top: 1.5px solid var(--border); padding-block: clamp(5rem,10vw,9rem); text-align: center; }
  .cta-eyebrow { display: block; text-align: center; margin-bottom: 0.75rem; }
  .cta-h2 { margin-bottom: 2.5rem; margin-inline: auto; max-width: 14ch; }

  /* ── FOOTER ────────────────────────────────────── */
  footer { background: var(--dark); padding: 2rem 0; border-top: 1px solid rgba(255,255,255,0.06); }
  .footer-inner { display: flex; justify-content: space-between; align-items: center; gap: 1rem; flex-wrap: wrap; }
  .footer-logo { font-size: var(--s-1); font-weight: 800; letter-spacing: -0.03em; color: var(--white); }
  .footer-logo span { color: var(--green); }
  .footer-copy { font-size: var(--s--1); color: rgba(255,255,255,0.4); }

  /* ── REVEAL ────────────────────────────────────── */
  :global(.reveal) { opacity: 0; transform: translateY(20px); transition: opacity 0.55s ease, transform 0.55s ease; }
  :global(.reveal.visible) { opacity: 1; transform: none; }

  /* ── RESPONSIVE ────────────────────────────────── */
  @media (max-width: 960px) {
    .hero-inner { grid-template-columns: 1fr; }
    .hero-visual { justify-content: center; margin-top: 2rem; }
    .hero-stack { margin-right: 0; max-width: 400px; }
    .pf-grid { grid-template-columns: 1fr; }
    .why-grid { grid-template-columns: 1fr 1fr; }
    .pricing-grid { grid-template-columns: 1fr; }
    .pricing-card { order: -1; }
  }
  @media (max-width: 600px) {
    .nav-cta { padding: 0.45rem 0.9rem; font-size: 0.78rem; }
    .pf-header { flex-direction: column; align-items: flex-start; }
    .why-grid { grid-template-columns: 1fr; }
    .hero-headline { letter-spacing: -0.03em; }
  }
</style>
