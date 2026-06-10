<!DOCTYPE html>
<html lang="es" style="background:#fff8f1 !important; color:#111 !important;">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="color-scheme" content="light only" />
  <meta name="supported-color-schemes" content="light" />
  <meta name="theme-color" content="#fff8f1" />
  <title>Construyendo para Vivir</title>
  <link href="https://fonts.googleapis.com/css2?family=Chewy&family=League+Spartan:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
  <link href="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.css" rel="stylesheet" />
  <style>
    /* ── Bloqueo total modo oscuro ── */
    :root { color-scheme: only light !important; }
    html, body, * { forced-color-adjust: none !important; }
    @media (prefers-color-scheme: dark) {
      html { background: #fff8f1 !important; color: #111 !important; filter: none !important; }
      body { background: #fff8f1 !important; color: #111 !important; }
      * { color: inherit !important; background-color: inherit !important; border-color: inherit !important; }
      header { background: #39503d !important; color: #fff8f1 !important; }
      header * { color: inherit !important; }
      .logo { color: #ffba38 !important; }
      nav a, .nav-mobile a { color: #fff8f1 !important; }
      nav a:hover { background: #ffba38 !important; color: #111 !important; }
      .section-title { color: #39503d !important; }
      .sobre-text p, .sobre-lista li, .contacto-intro { color: #333 !important; }
      .sobre-subtitulo, .sobre-lista li strong, .sobre-cta { color: #39503d !important; }
      .sobre-lista li::before { color: #ffba38 !important; }
      .contacto-intro a { color: #39503d !important; }
      .contacto-form { background: #fff8f1 !important; border-color: #e0d4c8 !important; }
      .contacto-form input, .contacto-form textarea { background: #f0e8df !important; color: #111 !important; border-color: #d0c8c0 !important; }
      .contacto-form label { color: #39503d !important; }
      .btn-enviar { background: #39503d !important; color: #ffba38 !important; }
      .redes { background: #39503d !important; }
      .redes .section-title { color: #ffba38 !important; }
      .red-card { color: #fff8f1 !important; background: rgba(255,255,255,0.1) !important; }
      footer { background: #2b3d2e !important; color: rgba(255,255,255,0.7) !important; }
      footer .footer-icons a { color: #ffba38 !important; }
      section { background: #fff8f1 !important; }
      .sobre-nosotros, .contacto { background: #fff8f1 !important; }
    }

    /* ── Reset & base ── */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { background: #fff8f1 !important; filter: none !important; scroll-behavior: smooth; }
    :root {
      --verde:   #39503d;
      --amarillo:#ffba38;
      --fondo:   #fff8f1;
      --negro:   #111;
      --blanco:  #fff8f1;
    }
    html { scroll-behavior: smooth; }
    body {
      font-family: 'League Spartan', sans-serif;
      background: var(--fondo);
      color: var(--negro);
    }

    /* ── GAGALIN via @font-face (Google Fonts no lo tiene, usamos fallback bold) ── */
    /* Cargamos Gagalin desde CDN de fonts si está disponible, fallback a Impact */
    @font-face {
      font-family: 'Gagalin';
      src: url('https://fonts.cdnfonts.com/s/15432/Gagalin-Regular.woff') format('woff');
      font-weight: normal;
    }
    h1, h2, .section-title {
      font-family: 'Gagalin', 'Impact', 'Arial Black', sans-serif;
      letter-spacing: 1px;
    }

    /* ── HEADER ── */
    header {
      background: var(--verde);
      position: sticky;
      top: 0;
      z-index: 100;
      box-shadow: 0 2px 8px rgba(0,0,0,0.25);
    }
    .header-inner {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 2rem;
      height: 70px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    .logo {
      font-family: 'Chewy', cursive;
      font-size: 1.7rem;
      color: var(--amarillo);
      text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000, 1px 1px 0 #000;
      text-decoration: none;
      white-space: nowrap;
    }
    nav { display: flex; gap: 0.25rem; align-items: center; }
    nav a {
      font-family: 'League Spartan', sans-serif;
      font-weight: 600;
      font-size: 0.95rem;
      color: var(--blanco);
      text-decoration: none;
      padding: 0.4rem 0.9rem;
      border-radius: 4px;
      transition: background 0.2s, color 0.2s;
      letter-spacing: 0.5px;
    }
    nav a:hover { background: var(--amarillo); color: var(--negro); }

    /* Hamburger */
    .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; padding: 4px; }
    .hamburger span { display: block; width: 24px; height: 2px; background: var(--blanco); border-radius: 2px; transition: all 0.3s; }
    .nav-mobile { display: none; flex-direction: column; background: var(--verde); padding: 0.5rem 2rem 1rem; }
    .nav-mobile a { color: var(--blanco); text-decoration: none; font-family: 'League Spartan', sans-serif; font-weight: 600; font-size: 1rem; padding: 0.6rem 0; border-bottom: 1px solid rgba(255,255,255,0.15); }
    .nav-mobile a:last-child { border-bottom: none; }
    .nav-mobile.open { display: flex; }

    @media (max-width: 700px) {
      nav { display: none; }
      .hamburger { display: flex; }
    }

    /* ── CARRUSEL ── */
    .carousel-section { position: relative; overflow: hidden; background: var(--fondo); }
    .carousel-track {
      display: flex;
      transition: transform 0.6s cubic-bezier(.4,0,.2,1);
    }
    .carousel-slide {
      min-width: 100%;
      height: 520px;
      position: relative;
    }
    .carousel-slide img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      display: block;
      object-position: center center;
    }
    @media (max-width: 700px) {
      .carousel-slide img { object-position: 67% center; }
    }
    .carousel-slide .slide-placeholder {
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: 'League Spartan', sans-serif;
      font-size: 1.1rem;
      color: rgba(255,255,255,0.6);
      background: #1a1a1a;
      flex-direction: column;
      gap: 0.5rem;
    }
    .carousel-slide .slide-placeholder svg { opacity: 0.3; }
    .carousel-overlay {
      display: none;
    }
    .carousel-btn {
      position: absolute;
      top: 50%; transform: translateY(-50%);
      background: rgba(8,111,58,0.75);
      border: 2px solid var(--amarillo);
      color: var(--amarillo);
      width: 44px; height: 44px;
      border-radius: 50%;
      font-size: 1.4rem;
      cursor: pointer;
      display: flex; align-items: center; justify-content: center;
      transition: background 0.2s;
      z-index: 10;
    }
    .carousel-btn:hover { background: var(--verde); }
    .carousel-btn.prev { left: 1.2rem; }
    .carousel-btn.next { right: 1.2rem; }
    .carousel-dots {
      position: absolute; bottom: 1rem; left: 50%; transform: translateX(-50%);
      display: flex; gap: 8px; z-index: 10;
    }
    .carousel-dots span {
      width: 10px; height: 10px;
      border-radius: 50%;
      background: rgba(255,255,255,0.45);
      cursor: pointer;
      transition: background 0.2s;
      border: 1.5px solid rgba(255,255,255,0.6);
    }
    .carousel-dots span.active { background: var(--amarillo); border-color: var(--amarillo); }

    /* ── SECTIONS base ── */
    section { padding: 4rem 2rem; }
    .section-inner { max-width: 860px; margin: 0 auto; }
    .section-title {
      font-size: clamp(1.8rem, 4vw, 2.6rem);
      color: var(--verde);
      margin-bottom: 1.5rem;
      position: relative;
      display: inline-block;
    }
    .section-title::after {
      content: '';
      display: block;
      width: 60px; height: 4px;
      background: var(--amarillo);
      border-radius: 2px;
      margin-top: 0.4rem;
    }

    /* ── SOBRE NOSOTROS + CONTACTO lado a lado ── */
    .sobre-contacto { background: var(--fondo); }
    .sobre-contacto-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 4rem;
      align-items: start;
      max-width: 1100px;
    }
    @media (max-width: 820px) {
      .sobre-contacto-grid { grid-template-columns: 1fr; gap: 3rem; }
    }

    /* ── SOBRE NOSOTROS ── */
    .sobre-nosotros { background: var(--fondo); }
    .sobre-nosotros .section-inner { max-width: 760px; }

    /* ── CONTACTO ── */
    .contacto { background: var(--fondo); }
    .contacto .section-inner { max-width: 760px; }
    .sobre-text p {
      font-size: 1.05rem;
      line-height: 1.8;
      color: #333;
      margin-bottom: 1rem;
    }
    .sobre-text p:last-child { margin-bottom: 0; }
    .sobre-subtitulo {
      font-family: 'Gagalin', 'Impact', 'Arial Black', sans-serif;
      color: var(--verde);
      font-size: 1.4rem;
      margin-top: 2rem;
      margin-bottom: 1rem;
      letter-spacing: 1px;
      display: inline-block;
      position: relative;
      padding-bottom: 0.3rem;
    }
    .sobre-subtitulo::after {
      content: '';
      display: block;
      width: 0;
      height: 3px;
      background: var(--amarillo);
      border-radius: 2px;
      margin-top: 0.3rem;
      transition: width 0.5s ease;
    }
    .sobre-subtitulo.aos-animate::after { width: 100%; }
    .sobre-lista {
      list-style: none;
      padding: 0;
      margin-bottom: 1.5rem;
      display: flex;
      flex-direction: column;
      gap: 0.85rem;
    }
    .sobre-lista li {
      font-size: 1.05rem;
      line-height: 1.7;
      color: #333;
      padding-left: 1.4rem;
      position: relative;
    }
    .sobre-lista li::before {
      content: '▸';
      color: var(--amarillo);
      position: absolute;
      left: 0;
      top: 0;
      font-size: 1rem;
    }
    .sobre-lista li strong { color: var(--verde); }
    .sobre-cta {
      font-family: 'Gagalin', 'Impact', 'Arial Black', sans-serif;
      font-size: 1.25rem;
      color: var(--verde);
      margin-top: 2rem;
      font-style: normal;
      letter-spacing: 0.5px;
    }
    .sobre-badge {
      background: var(--verde);
      color: var(--blanco);
      border-radius: 12px;
      padding: 2rem;
      text-align: center;
    }
    .sobre-badge .number {
      font-family: 'Gagalin', 'Impact', sans-serif;
      font-size: 3.5rem;
      color: var(--amarillo);
      line-height: 1;
    }
    .sobre-badge .label {
      font-family: 'League Spartan', sans-serif;
      font-size: 0.95rem;
      color: rgba(255,255,255,0.85);
      margin-top: 0.5rem;
      font-weight: 400;
    }
    .badges-grid { display: flex; flex-direction: column; gap: 1rem; }

    @media (max-width: 680px) {
      .sobre-nosotros .section-inner { grid-template-columns: 1fr; }
    }

    /* ── CONTACTO ── */
    .contacto-intro {
      font-size: 1.05rem;
      line-height: 1.8;
      color: #333;
      margin-bottom: 2rem;
    }
    .contacto-intro a {
      color: var(--verde);
      font-weight: 600;
      text-decoration: underline;
      text-underline-offset: 3px;
    }
    .contacto-intro a:hover { color: #253829; }
    .contacto-form {
      background: var(--fondo);
      border-radius: 12px;
      padding: 2.5rem;
      border: 1.5px solid #e0d4c8;
      max-width: 560px;
    }
    .contacto-form label {
      display: block;
      font-weight: 600;
      font-size: 0.9rem;
      color: var(--verde);
      margin-bottom: 0.35rem;
      letter-spacing: 0.5px;
    }
    .contacto-form input,
    .contacto-form textarea {
      width: 100%;
      padding: 0.75rem 1rem;
      border: 1.5px solid #d0c8c0;
      border-radius: 6px;
      font-family: 'League Spartan', sans-serif;
      font-size: 1rem;
      background: #f0e8df;
      color: var(--negro);
      margin-bottom: 1.25rem;
      transition: border-color 0.2s;
      outline: none;
    }
    .contacto-form input:focus,
    .contacto-form textarea:focus { border-color: var(--verde); }
    .contacto-form textarea { resize: vertical; min-height: 120px; }
    .btn-enviar {
      background: var(--verde);
      color: var(--amarillo);
      font-family: 'Gagalin', 'Impact', sans-serif;
      font-size: 1.1rem;
      letter-spacing: 1px;
      padding: 0.75rem 2.5rem;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      transition: background 0.2s, transform 0.1s;
    }
    .btn-enviar:hover { background: #253829; }
    .btn-enviar:active { transform: scale(0.98); }

    /* ── REDES ── */
    .redes { background: var(--verde); text-align: center; }
    .redes .section-title { color: var(--amarillo); }
    .redes .section-title::after { background: var(--blanco); }
    .redes-grid {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 1.5rem;
      margin-top: 2rem;
    }
    .red-card {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 0.6rem;
      text-decoration: none;
      background: rgba(255,255,255,0.1);
      border: 2px solid rgba(255,186,56,0.4);
      border-radius: 12px;
      padding: 1.5rem 2rem;
      color: var(--blanco);
      transition: background 0.2s, border-color 0.2s, transform 0.2s;
      min-width: 130px;
    }
    .red-card:hover {
      background: rgba(255,186,56,0.2);
      border-color: var(--amarillo);
      transform: translateY(-4px);
    }
    .red-card svg { width: 40px; height: 40px; }
    .red-card span {
      font-family: 'League Spartan', sans-serif;
      font-weight: 600;
      font-size: 0.95rem;
      letter-spacing: 0.5px;
    }

    /* ── FOOTER ── */
    footer {
      background: #2b3d2e;
      color: rgba(255,255,255,0.7);
      text-align: center;
      padding: 1.5rem 2rem;
      font-size: 0.88rem;
    }
    footer .footer-icons {
      display: flex;
      justify-content: center;
      gap: 1.2rem;
      margin-bottom: 0.75rem;
    }
    footer .footer-icons a {
      color: var(--amarillo);
      transition: color 0.2s, transform 0.2s;
      display: inline-block;
    }
    footer .footer-icons a:hover { color: var(--blanco); transform: scale(1.15); }
    footer .footer-icons svg { width: 24px; height: 24px; display: block; }

    /* ── KEN BURNS ── */
    @keyframes kenburns {
      0%   { transform: scale(1)    translate(0, 0); }
      50%  { transform: scale(1.07) translate(-1%, -1%); }
      100% { transform: scale(1)    translate(0, 0); }
    }
    .carousel-slide img { animation: kenburns 12s ease-in-out infinite; }
    @media (prefers-reduced-motion: reduce) {
      .carousel-slide img { animation: none; }
    }

    /* ── WAVE entre carrusel y sobre nosotros ── */
    .wave-divider { display: block; width: 100%; overflow: hidden; line-height: 0; margin-bottom: -2px; }
    .wave-divider svg { display: block; width: 100%; }

    /* ── HOVER mejorado en botón enviar ── */
    .btn-enviar { transition: background 0.25s, transform 0.15s, letter-spacing 0.2s; }
    .btn-enviar:hover { letter-spacing: 2px; }

    /* ── HOVER mejorado en red-card ── */
    .red-card { transition: background 0.25s, border-color 0.25s, transform 0.25s, box-shadow 0.25s; }
    .red-card:hover { box-shadow: 0 8px 24px rgba(0,0,0,0.2); }

    /* ── FADE IN del header al cargar ── */
    @keyframes fadedown {
      from { opacity: 0; transform: translateY(-16px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    header { animation: fadedown 0.6s ease both; }

    /* ── Línea animada bajo section-title ── */
    .section-title::after {
      transition: width 0.4s ease;
      width: 60px;
    }
    .section-title:hover::after { width: 100%; }
  </style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="header-inner">
    <a href="#inicio" class="logo">Construyendo para Vivir</a>
    <nav>
      <a href="#inicio">Inicio</a>
      <a href="#sobre-nosotros">Sobre nosotros</a>
      <a href="#contacto">Contacto</a>
      <a href="#redes">Redes</a>
    </nav>
    <div class="hamburger" onclick="toggleMenu()" aria-label="Menú">
      <span></span><span></span><span></span>
    </div>
  </div>
  <div class="nav-mobile" id="navMobile">
    <a href="#inicio" onclick="toggleMenu()">Inicio</a>
    <a href="#sobre-nosotros" onclick="toggleMenu()">Sobre nosotros</a>
    <a href="#contacto" onclick="toggleMenu()">Contacto</a>
    <a href="#redes" onclick="toggleMenu()">Redes</a>
  </div>
</header>

<!-- CARRUSEL -->
<section class="carousel-section" id="inicio">
  <div class="carousel-track" id="carouselTrack">

    <!-- Slide 1: imagen real -->
    <div class="carousel-slide">
      <img src="https://www.image2url.com/r2/default/images/1781050003547-ba760302-0d22-4d6e-a495-3d17a780c13e.jpg" alt="Construyendo para Vivir" />
    </div>

  </div>

</section>

<div class="wave-divider">
  <svg viewBox="0 0 1440 60" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none">
    <path d="M0,30 C360,60 1080,0 1440,30 L1440,60 L0,60 Z" fill="#fff8f1"/>
  </svg>
</div>

<!-- SOBRE NOSOTROS -->
<section class="sobre-nosotros" id="sobre-nosotros">
  <div class="section-inner">
    <h2 class="section-title" data-aos="fade-right" data-aos-duration="700">Sobre nosotros</h2>
    <div class="sobre-text">
      <p data-aos="fade-up" data-aos-duration="700" data-aos-delay="100">
        Somos Santi y Flor, estamos construyendo nuestro hogar en un contenedor de 40 pies para irnos a vivir al campo. Queremos salir del sistema tradicional de los alquileres caros y los préstamos de por vida para armar una vida más libre, simple y conectada con la naturaleza.
      </p>
      <p data-aos="fade-up" data-aos-duration="700" data-aos-delay="200">
        No somos arquitectos, ingenieros ni expertos en construcción. Somos una pareja común con trabajos, facultad y rutinas exigentes que un día decidió dejar de postergar sus sueños y animarse a probar. Todo lo que sabemos lo vamos aprendiendo paso a paso, en nuestros ratos libres y fines de semana.
      </p>
      <p class="sobre-subtitulo" data-aos="fade-right" data-aos-duration="800" data-aos-delay="300">Qué vas a encontrar acá:</p>
      <ul class="sobre-lista">
        <li data-aos="fade-up" data-aos-duration="600" data-aos-delay="350"><strong>El proceso real:</strong> Documentamos cada avance, cada acierto y también los pequeños errores de obra de forma honesta, sin filtros ni dramas inflados.</li>
        <li data-aos="fade-up" data-aos-duration="600" data-aos-delay="450"><strong>Datos útiles:</strong> Compartimos presupuestos reales, lo que nos cuestan las herramientas y los materiales en Uruguay, y cómo resolvemos temas clave como la aislación térmica.</li>
        <li data-aos="fade-up" data-aos-duration="600" data-aos-delay="550"><strong>Inspiración y comunidad:</strong> Creamos este espacio para ayudarte a perder el miedo y demostrarte que, si tenés ganas, vos también podés empezar.</li>
      </ul>
      <p class="sobre-cta" data-aos="zoom-in-up" data-aos-duration="800" data-aos-delay="650">¿Y vos? ¿Te irías a vivir a un contenedor? ¡Acompañanos en esta aventura!</p>
    </div>
  </div>
</section>

<!-- CONTACTO -->
<section class="contacto" id="contacto">
  <div class="section-inner">
    <h2 class="section-title" data-aos="fade-right" data-aos-duration="700">Contacto</h2>
    <p class="contacto-intro" data-aos="fade-up" data-aos-duration="700" data-aos-delay="100">Si te interesa trabajar con nosotros o hacer colaboraciones podés escribirnos a <a href="mailto:contacto@construyendoparavivir.com">contacto@construyendoparavivir.com</a> o llenando el formulario.</p>
    <div class="contacto-form" data-aos="fade-up" data-aos-duration="700" data-aos-delay="200">
      <div>
        <label for="nombre">Nombre</label>
        <input type="text" id="nombre" placeholder="Tu nombre completo" />
      </div>
      <div>
        <label for="email">Correo electrónico</label>
        <input type="email" id="email" placeholder="tu@correo.com" />
      </div>
      <div>
        <label for="mensaje">Mensaje</label>
        <textarea id="mensaje" placeholder="Contanos en qué podemos ayudarte..."></textarea>
      </div>
      <button class="btn-enviar" type="button">Enviar mensaje</button>
    </div>
  </div>
</section>

<!-- REDES -->
<section class="redes" id="redes">
  <div class="section-inner">
    <h2 class="section-title" data-aos="fade-up" data-aos-duration="700">Seguinos en redes</h2>
    <div class="redes-grid">

      <a class="red-card" href="https://www.instagram.com/construyendoparavivir/" target="_blank" rel="noopener" data-aos="zoom-in" data-aos-duration="600" data-aos-delay="100">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
          <rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="1" fill="currentColor" stroke="none"/>
        </svg>
        <span>Instagram</span>
      </a>

      <a class="red-card" href="https://www.facebook.com/profile.php?id=61589993397244&locale=es_LA" target="_blank" rel="noopener" data-aos="zoom-in" data-aos-duration="600" data-aos-delay="200">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
          <path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"/>
        </svg>
        <span>Facebook</span>
      </a>

      <a class="red-card" href="https://www.tiktok.com/discover/construyendo-para-vivir" target="_blank" rel="noopener" data-aos="zoom-in" data-aos-duration="600" data-aos-delay="300">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
          <path d="M9 12a4 4 0 1 0 4 4V4a5 5 0 0 0 5 5"/>
        </svg>
        <span>TikTok</span>
      </a>

      <a class="red-card" href="https://www.youtube.com/@ConstruyendoParaVivir" target="_blank" rel="noopener" data-aos="zoom-in" data-aos-duration="600" data-aos-delay="400">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
          <path d="M22.54 6.42A2.78 2.78 0 0 0 20.59 4.5C19 4 12 4 12 4s-7 0-8.59.5A2.78 2.78 0 0 0 1.46 6.42 29 29 0 0 0 1 12a29 29 0 0 0 .46 5.58A2.78 2.78 0 0 0 3.41 19.5C5 20 12 20 12 20s7 0 8.59-.5a2.78 2.78 0 0 0 1.95-1.92A29 29 0 0 0 23 12a29 29 0 0 0-.46-5.58z"/>
          <polygon points="9.75 15.02 15.5 12 9.75 8.98 9.75 15.02"/>
        </svg>
        <span>YouTube</span>
      </a>

    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-icons">
    <a href="https://www.instagram.com/construyendoparavivir/" target="_blank" rel="noopener" aria-label="Instagram">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
        <rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="1" fill="currentColor" stroke="none"/>
      </svg>
    </a>
    <a href="https://www.facebook.com/profile.php?id=61589993397244&locale=es_LA" target="_blank" rel="noopener" aria-label="Facebook">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
        <path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"/>
      </svg>
    </a>
    <a href="https://www.tiktok.com/discover/construyendo-para-vivir" target="_blank" rel="noopener" aria-label="TikTok">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
        <path d="M9 12a4 4 0 1 0 4 4V4a5 5 0 0 0 5 5"/>
      </svg>
    </a>
    <a href="https://www.youtube.com/@ConstruyendoParaVivir" target="_blank" rel="noopener" aria-label="YouTube">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
        <path d="M22.54 6.42A2.78 2.78 0 0 0 20.59 4.5C19 4 12 4 12 4s-7 0-8.59.5A2.78 2.78 0 0 0 1.46 6.42 29 29 0 0 0 1 12a29 29 0 0 0 .46 5.58A2.78 2.78 0 0 0 3.41 19.5C5 20 20 20 20 20s7 0 8.59-.5a2.78 2.78 0 0 0 1.95-1.92A29 29 0 0 0 23 12a29 29 0 0 0-.46-5.58z"/>
        <polygon points="9.75 15.02 15.5 12 9.75 8.98 9.75 15.02"/>
      </svg>
    </a>
  </div>
  <p>&copy; 2025 Construyendo para Vivir. Todos los derechos reservados.</p>
</footer>

<script src="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.js"></script>
<script>
  // Menú hamburguesa
  function toggleMenu() {
    document.getElementById('navMobile').classList.toggle('open');
  }

  // Inicializar AOS
  AOS.init({
    once: true,
    offset: 60,
    easing: 'ease-out-cubic'
  });
</script>
</body>
</html>
