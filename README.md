# antigravity-ide17
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Portal Inmobiliario de vanguardia para compra, venta y alquiler de inmuebles de lujo y residenciales.">
    <meta name="keywords" content="inmobiliaria, bienes raices, real estate, casas, departamentos, hipoteca, alquiler, compra">
    <title>HabitatPrime - Portal Inmobiliario & Analítica Residencial</title>

    <!-- Google Fonts: Poppins & Open Sans -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,400;0,600;0,700;1,400&family=Poppins:wght@500;600;700;800&display=swap" rel="stylesheet">

    <style>
        /* ==========================================================================
           1. CSS CUSTOM PROPERTIES & DESIGN SYSTEM
           ========================================================================== */
        :root {
            --color-primary: #065F46;
            --color-primary-hover: #044E39;
            --color-primary-light: #D1FAE5;
            --color-secondary: #0284C7;
            --color-secondary-hover: #0369A1;
            --color-bg: #F0FDF4;
            --color-surface: #FFFFFF;
            --color-surface-hover: #F8FAFC;
            --color-text-main: #1F2937;
            --color-text-muted: #6B7280;
            --color-status-available: #16A34A;
            --color-status-pending: #D97706;
            --color-border: #E5E7EB;
            --color-danger: #DC2626;

            --font-title: 'Poppins', sans-serif;
            --font-body: 'Open Sans', sans-serif;

            --spacing-xs: 4px;
            --spacing-sm: 8px;
            --spacing-md: 16px;
            --spacing-lg: 24px;
            --spacing-xl: 32px;
            --spacing-2xl: 48px;

            --radius-sm: 6px;
            --radius-md: 10px;
            --radius-lg: 16px;
            --radius-full: 9999px;

            --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
            --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
            --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
            --shadow-float: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
        }

        /* RESET & BASE */
        *, *::before, *::after {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: var(--font-body);
            background-color: var(--color-bg);
            color: var(--color-text-main);
            line-height: 1.6;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        h1, h2, h3, h4, h5, h6 {
            font-family: var(--font-title);
            color: var(--color-primary);
            line-height: 1.25;
        }

        a { color: inherit; text-decoration: none; }
        button, input, select, textarea { font-family: inherit; font-size: inherit; color: inherit; }
        button { cursor: pointer; border: none; background: none; }

        /* ==========================================================================
           2. NAVIGATION & HEADER BLOCK (BEM)
           ========================================================================== */
        .header {
            background-color: var(--color-surface);
            border-bottom: 1px solid var(--color-border);
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: var(--shadow-sm);
        }

        .header__container {
            max-width: 1400px;
            margin: 0 auto;
            padding: var(--spacing-md) var(--spacing-lg);
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: var(--spacing-md);
        }

        .header__logo {
            display: flex;
            align-items: center;
            gap: var(--spacing-sm);
            font-family: var(--font-title);
            font-size: 1.35rem;
            font-weight: 800;
            color: var(--color-primary);
        }

        .header__logo-icon {
            width: 32px;
            height: 32px;
            fill: var(--color-primary);
        }

        .nav {
            display: flex;
            align-items: center;
        }

        .nav__list {
            display: flex;
            list-style: none;
            gap: var(--spacing-sm);
            overflow-x: auto;
            max-width: 850px;
            padding: 4px 0;
        }

        .nav__item { white-space: nowrap; }

        .nav__link {
            font-family: var(--font-title);
            font-size: 0.85rem;
            font-weight: 600;
            color: var(--color-text-muted);
            padding: var(--spacing-sm) var(--spacing-md);
            border-radius: var(--radius-md);
            transition: all 0.2s ease;
        }

        .nav__link:hover {
            color: var(--color-primary);
            background-color: var(--color-primary-light);
        }

        .nav__link--active {
            color: var(--color-surface);
            background-color: var(--color-primary);
        }

        .nav__link--active:hover {
            color: var(--color-surface);
            background-color: var(--color-primary-hover);
        }

        .header__actions {
            display: flex;
            align-items: center;
            gap: var(--spacing-md);
        }

        .fav-badge {
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background-color: var(--color-bg);
            border-radius: var(--radius-full);
            cursor: pointer;
            transition: background 0.2s;
        }

        .fav-badge:hover { background-color: var(--color-primary-light); }

        .fav-badge__count {
            position: absolute;
            top: -2px;
            right: -2px;
            background-color: var(--color-secondary);
            color: var(--color-surface);
            font-size: 0.7rem;
            font-weight: 700;
            width: 18px;
            height: 18px;
            border-radius: var(--radius-full);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* ==========================================================================
           3. LAYOUT & VIEWS SYSTEM
           ========================================================================== */
        .main-layout {
            max-width: 1400px;
            width: 100%;
            margin: 0 auto;
            padding: var(--spacing-xl) var(--spacing-lg);
            flex: 1;
        }

        .view {
            display: none;
            animation: fadeIn 0.3s ease-in-out;
        }

        .view--active { display: block; }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(6px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .view-header {
            margin-bottom: var(--spacing-xl);
        }

        .view-header__title {
            font-size: 2rem;
            font-weight: 800;
            color: var(--color-primary);
        }

        .view-header__subtitle {
            color: var(--color-text-muted);
            font-size: 0.95rem;
            margin-top: var(--spacing-xs);
        }

        /* UI COMPONENTS: BUTTONS, CARDS, FORMS */
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: var(--spacing-sm);
            padding: var(--spacing-md) var(--spacing-xl);
            background-color: var(--color-primary);
            color: var(--color-surface);
            font-family: var(--font-title);
            font-weight: 600;
            font-size: 0.9rem;
            border-radius: var(--radius-md);
            transition: all 0.2s ease;
            box-shadow: var(--shadow-sm);
        }

        .btn:hover {
            background-color: var(--color-primary-hover);
            transform: translateY(-1px);
            box-shadow: var(--shadow-md);
        }

        .btn--secondary {
            background-color: var(--color-secondary);
        }

        .btn--secondary:hover {
            background-color: var(--color-secondary-hover);
        }

        .btn--outline {
            background-color: transparent;
            border: 2px solid var(--color-primary);
            color: var(--color-primary);
            box-shadow: none;
        }

        .btn--outline:hover {
            background-color: var(--color-primary-light);
            transform: none;
        }

        .card {
            background-color: var(--color-surface);
            border: 1px solid var(--color-border);
            border-radius: var(--radius-lg);
            padding: var(--spacing-xl);
            box-shadow: var(--shadow-md);
        }

        .grid-2 { display: grid; grid-template-columns: repeat(2, 1fr); gap: var(--spacing-xl); }
        .grid-3 { display: grid; grid-template-columns: repeat(3, 1fr); gap: var(--spacing-xl); }
        .grid-4 { display: grid; grid-template-columns: repeat(4, 1fr); gap: var(--spacing-lg); }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: var(--spacing-xs);
            margin-bottom: var(--spacing-md);
        }

        .form-label {
            font-size: 0.85rem;
            font-weight: 700;
            color: var(--color-text-main);
        }

        .form-input, .form-select, .form-textarea {
            width: 100%;
            background-color: var(--color-surface);
            border: 1.5px solid var(--color-border);
            border-radius: var(--radius-md);
            padding: var(--spacing-md);
            color: var(--color-text-main);
            outline: none;
            transition: border-color 0.2s ease, box-shadow 0.2s ease;
        }

        .form-input:focus, .form-select:focus, .form-textarea:focus {
            border-color: var(--color-secondary);
            box-shadow: 0 0 0 3px rgba(2, 132, 199, 0.15);
        }

        /* ==========================================================================
           4. PAGE SPECIFIC STYLES (10 PAGES)
           ========================================================================== */
        
        /* PAGE 1: SEARCH HERO */
        .search-hero {
            background: linear-gradient(135deg, rgba(6, 95, 70, 0.95), rgba(2, 132, 199, 0.85)), url('https://images.unsplash.com/photo-1600596542815-ffad4c1539a9?auto=format&fit=crop&w=1600&q=80') center/cover no-repeat;
            border-radius: var(--radius-lg);
            padding: var(--spacing-2xl) var(--spacing-xl);
            color: var(--color-surface);
            text-align: center;
            box-shadow: var(--shadow-lg);
            margin-bottom: var(--spacing-xl);
        }

        .search-hero__title {
            color: var(--color-surface);
            font-size: 2.75rem;
            font-weight: 800;
            margin-bottom: var(--spacing-md);
        }

        .search-hero__subtitle {
            font-size: 1.1rem;
            max-width: 650px;
            margin: 0 auto var(--spacing-xl) auto;
            opacity: 0.9;
        }

        .search-box {
            background-color: var(--color-surface);
            border-radius: var(--radius-lg);
            padding: var(--spacing-lg);
            box-shadow: var(--shadow-float);
            max-width: 1000px;
            margin: 0 auto;
            color: var(--color-text-main);
            text-align: left;
        }

        /* PROPERTY CARD (BEM) */
        .property-card {
            background-color: var(--color-surface);
            border: 1px solid var(--color-border);
            border-radius: var(--radius-lg);
            overflow: hidden;
            transition: transform 0.25s ease, box-shadow 0.25s ease;
            display: flex;
            flex-direction: column;
            position: relative;
        }

        .property-card:hover {
            transform: translateY(-4px);
            box-shadow: var(--shadow-lg);
        }

        .property-card__image-wrap {
            position: relative;
            height: 220px;
            background-color: var(--color-border);
            overflow: hidden;
        }

        .property-card__image {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.4s ease;
        }

        .property-card:hover .property-card__image {
            transform: scale(1.05);
        }

        .property-card__badge {
            position: absolute;
            top: var(--spacing-md);
            left: var(--spacing-md);
            background-color: var(--color-status-available);
            color: var(--color-surface);
            font-size: 0.75rem;
            font-weight: 700;
            padding: 4px var(--spacing-md);
            border-radius: var(--radius-full);
            text-transform: uppercase;
        }

        .property-card__fav-btn {
            position: absolute;
            top: var(--spacing-md);
            right: var(--spacing-md);
            background-color: rgba(255, 255, 255, 0.9);
            width: 36px;
            height: 36px;
            border-radius: var(--radius-full);
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: var(--shadow-sm);
            transition: background 0.2s, transform 0.2s;
        }

        .property-card__fav-btn:hover {
            transform: scale(1.1);
            background-color: var(--color-surface);
        }

        .property-card__fav-btn--active svg {
            fill: var(--color-danger);
            stroke: var(--color-danger);
        }

        .property-card__content {
            padding: var(--spacing-lg);
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        .property-card__price {
            font-family: var(--font-title);
            font-size: 1.4rem;
            font-weight: 800;
            color: var(--color-primary);
            margin-bottom: var(--spacing-xs);
        }

        .property-card__title {
            font-size: 1.1rem;
            font-weight: 700;
            margin-bottom: var(--spacing-xs);
            color: var(--color-text-main);
        }

        .property-card__location {
            font-size: 0.85rem;
            color: var(--color-text-muted);
            margin-bottom: var(--spacing-md);
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .property-card__features {
            display: flex;
            gap: var(--spacing-md);
            padding-top: var(--spacing-md);
            border-top: 1px solid var(--color-border);
            font-size: 0.85rem;
            color: var(--color-text-muted);
            margin-top: auto;
        }

        .property-card__feature-item {
            display: flex;
            align-items: center;
            gap: 6px;
            font-weight: 600;
        }

        /* SIMULATED MAP VIEW */
        .map-simulated {
            background-color: #E2E8F0;
            border-radius: var(--radius-lg);
            height: 500px;
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            border: 1px solid var(--color-border);
        }

        .map-marker {
            position: absolute;
            background-color: var(--color-primary);
            color: var(--color-surface);
            padding: 6px 12px;
            border-radius: var(--radius-full);
            font-weight: 700;
            font-size: 0.8rem;
            box-shadow: var(--shadow-md);
            cursor: pointer;
            transition: transform 0.2s;
        }

        .map-marker:hover {
            transform: scale(1.15);
            background-color: var(--color-secondary);
            z-index: 10;
        }

        /* MORTGAGE CALCULATOR */
        .calc-range {
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        .calc-range__header {
            display: flex;
            justify-content: space-between;
            font-weight: 700;
            font-size: 0.9rem;
        }

        .calc-result-box {
            background: linear-gradient(135deg, var(--color-primary), var(--color-primary-hover));
            color: var(--color-surface);
            padding: var(--spacing-xl);
            border-radius: var(--radius-lg);
            text-align: center;
            box-shadow: var(--shadow-md);
        }

        .calc-result-box__price {
            font-size: 2.5rem;
            font-weight: 800;
            font-family: var(--font-title);
            margin: var(--spacing-sm) 0;
        }

        /* TOAST NOTIFICATIONS */
        .toast-container {
            position: fixed;
            bottom: var(--spacing-xl);
            right: var(--spacing-xl);
            z-index: 1000;
            display: flex;
            flex-direction: column;
            gap: var(--spacing-sm);
        }

        .toast {
            background-color: var(--color-surface);
            border-left: 4px solid var(--color-secondary);
            padding: var(--spacing-md) var(--spacing-lg);
            border-radius: var(--radius-md);
            box-shadow: var(--shadow-lg);
            font-weight: 600;
            font-size: 0.9rem;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        /* FOOTER */
        .footer {
            background-color: var(--color-primary);
            color: var(--color-surface);
            padding: var(--spacing-2xl) var(--spacing-lg) var(--spacing-lg) var(--spacing-lg);
            margin-top: var(--spacing-2xl);
        }

        .footer__container {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 2fr repeat(3, 1fr);
            gap: var(--spacing-2xl);
            padding-bottom: var(--spacing-xl);
            border-bottom: 1px solid rgba(255, 255, 255, 0.15);
        }

        .footer__title {
            color: var(--color-surface);
            font-size: 1.1rem;
            margin-bottom: var(--spacing-md);
        }

        .footer__list {
            list-style: none;
            display: flex;
            flex-direction: column;
            gap: var(--spacing-sm);
            font-size: 0.9rem;
            opacity: 0.85;
        }

        .footer__bottom {
            max-width: 1400px;
            margin: var(--spacing-md) auto 0 auto;
            text-align: center;
            font-size: 0.85rem;
            opacity: 0.7;
        }

        @media (max-width: 1024px) {
            .grid-2, .grid-3, .grid-4 { grid-template-columns: 1fr; }
            .footer__container { grid-template-columns: 1fr; gap: var(--spacing-xl); }
            .search-hero__title { font-size: 2rem; }
        }
    </style>
</head>
<body>

    <!-- ==========================================================================
       HEADER & GLOBAL NAVIGATION
       ========================================================================== -->
    <header class="header" role="banner">
        <div class="header__container">
            <a href="#search" class="header__logo" onclick="navigateTo('search')">
                <svg class="header__logo-icon" viewBox="0 0 24 24">
                    <path d="M12 3L2 12h3v8h6v-6h2v6h6v-8h3L12 3z"/>
                </svg>
                <span>HabitatPrime</span>
            </a>

            <nav class="nav" role="navigation" aria-label="Navegación del sitio">
                <ul class="nav__list">
                    <li class="nav__item"><button class="nav__link nav__link--active" id="nav-search" onclick="navigateTo('search')">1. Buscador</button></li>
                    <li class="nav__item"><button class="nav__link" id="nav-listings" onclick="navigateTo('listings')">2. Listado</button></li>
                    <li class="nav__item"><button class="nav__link" id="nav-details" onclick="navigateTo('details')">3. Detalle Inmueble</button></li>
                    <li class="nav__item"><button class="nav__link" id="nav-mortgage" onclick="navigateTo('mortgage')">4. Hipoteca</button></li>
                    <li class="nav__item"><button class="nav__link" id="nav-visit" onclick="navigateTo('visit')">5. Agendar Visita</button></li>
                    <li class="nav__item"><button class="nav__link" id="nav-publish" onclick="navigateTo('publish')">6. Publicar</button></li>
                    <li class="nav__item"><button class="nav__link" id="nav-agents" onclick="navigateTo('agents')">7. Agentes</button></li>
                    <li class="nav__item"><button class="nav__link" id="nav-portal" onclick="navigateTo('portal')">8. Mi Portal</button></li>
                    <li class="nav__item"><button class="nav__link" id="nav-favorites" onclick="navigateTo('favorites')">9. Favoritos</button></li>
                    <li class="nav__item"><button class="nav__link" id="nav-contact" onclick="navigateTo('contact')">10. Contacto</button></li>
                </ul>
            </nav>

            <div class="header__actions">
                <div class="fav-badge" onclick="navigateTo('favorites')" title="Ver Favoritos Guardados">
                    <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path>
                    </svg>
                    <span class="fav-badge__count" id="fav-count">0</span>
                </div>
                <button class="btn btn--secondary" onclick="navigateTo('publish')">+ Publicar</button>
            </div>
        </div>
    </header>

    <!-- ==========================================================================
       MAIN CONTENT CONTAINER (SPA VIEWS)
       ========================================================================== -->
    <main class="main-layout" id="main-content">

        <!-- PAGE 1: BUSCADOR PRINCIPAL -->
        <section id="view-search" class="view view--active">
            <div class="search-hero">
                <h1 class="search-hero__title">Encuentra el hogar perfecto para tu futuro</h1>
                <p class="search-hero__subtitle">Explora miles de propiedades exclusivas en compra, venta y alquiler con garantías certificadas y asesoría personalizada.</p>
                
                <div class="search-box">
                    <form onsubmit="handleHeroSearch(event)" class="grid-4" style="align-items:end;">
                        <div class="form-group" style="margin-bottom:0;">
                            <label class="form-label">Ubicación o Ciudad</label>
                            <input type="text" id="search-location" class="form-input" placeholder="Ej: Madrid, Polanco, Santiago...">
                        </div>
                        <div class="form-group" style="margin-bottom:0;">
                            <label class="form-label">Tipo de Operación</label>
                            <select id="search-type" class="form-select">
                                <option value="venta">Comprar (Venta)</option>
                                <option value="alquiler">Rentar (Alquiler)</option>
                            </select>
                        </div>
                        <div class="form-group" style="margin-bottom:0;">
                            <label class="form-label">Precio Máximo ($)</label>
                            <input type="number" id="search-max-price" class="form-input" placeholder="Ej: 500,000">
                        </div>
                        <button type="submit" class="btn btn--secondary" style="height:48px;">Buscar Propiedades</button>
                    </form>
                </div>
            </div>

            <div class="view-header" style="margin-top:var(--spacing-2xl);">
                <h2 class="view-header__title">Propiedades Destacadas de la Semana</h2>
                <p class="view-header__subtitle">Selección VIP elegida por nuestros expertos analistas inmobiliarios</p>
            </div>

            <div class="grid-3" id="hero-featured-grid"></div>
        </section>

        <!-- PAGE 2: LISTADO DE PROPIEDADES -->
        <section id="view-listings" class="view">
            <div class="view-header">
                <h1 class="view-header__title">Catálogo Completo de Inmuebles</h1>
                <p class="view-header__subtitle">Filtra y explora las mejores alternativas residenciales del mercado</p>
            </div>

            <div class="grid-4" style="grid-template-columns: 280px 1fr; margin-bottom:var(--spacing-xl);">
                <!-- Filtros Laterales -->
                <aside class="card">
                    <h3 style="margin-bottom:var(--spacing-md); font-size:1.1rem;">Filtros Avanzados</h3>
                    <div class="form-group">
                        <label class="form-label">Dormitorios</label>
                        <select id="filter-beds" class="form-select" onchange="applyFilters()">
                            <option value="ALL">Cualquier cantidad</option>
                            <option value="1">1+ Dormitorios</option>
                            <option value="2">2+ Dormitorios</option>
                            <option value="3">3+ Dormitorios</option>
                            <option value="4">4+ Dormitorios</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Tipo de Inmueble</label>
                        <select id="filter-property-type" class="form-select" onchange="applyFilters()">
                            <option value="ALL">Todos los tipos</option>
                            <option value="Casa">Casa Unifamiliar</option>
                            <option value="Departamento">Departamento / Penthouse</option>
                            <option value="Villa">Villa de Lujo</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Amenidades</label>
                        <label style="font-size:0.85rem;"><input type="checkbox" id="pool-check" onchange="applyFilters()"> Alberca / Piscina</label>
                        <label style="font-size:0.85rem;"><input type="checkbox" id="garage-check" onchange="applyFilters()"> Estacionamiento</label>
                    </div>
                </aside>

                <!-- Grid & Simulated Map -->
                <div>
                    <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:var(--spacing-md);">
                        <span style="font-weight:700;" id="results-count-label">Mostrando propiedades disponibles</span>
                        <div>
                            <button class="btn btn--outline" onclick="toggleMapView(false)">Grid Lista</button>
                            <button class="btn btn--outline" onclick="toggleMapView(true)">Vista Mapa</button>
                        </div>
                    </div>

                    <div id="listings-grid-view" class="grid-3"></div>

                    <div id="listings-map-view" class="map-simulated" style="display:none;">
                        <span style="position:absolute; top:12px; left:12px; background:white; padding:4px 12px; border-radius:6px; font-weight:700; font-size:0.8rem;">Modo Mapa Interactivo (Coordenadas Reales)</span>
                        <div class="map-marker" style="top:25%; left:35%;" onclick="openPropertyDetail(1)">$450,000</div>
                        <div class="map-marker" style="top:45%; left:60%;" onclick="openPropertyDetail(2)">$780,000</div>
                        <div class="map-marker" style="top:70%; left:25%;" onclick="openPropertyDetail(3)">$290,000</div>
                        <div class="map-marker" style="top:55%; left:75%;" onclick="openPropertyDetail(4)">$1,200,000</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- PAGE 3: VISTA DETALLADA DE INMUEBLE (Con Schema.org Microdatos) -->
        <section id="view-details" class="view">
            <div id="property-detail-container" itemscope itemtype="https://schema.org/SingleFamilyResidence">
                <!-- Inyectado dinámicamente vía JS -->
            </div>
        </section>

        <!-- PAGE 4: CALCULADORA HIPOTECARIA INTERACTIVA -->
        <section id="view-mortgage" class="view">
            <div class="view-header">
                <h1 class="view-header__title">Calculadora Hipotecaria Financiera</h1>
                <p class="view-header__subtitle">Estima tu cuota mensual de amortización en tiempo real ajustando los parámetros</p>
            </div>

            <div class="grid-2">
                <div class="card">
                    <h3 style="margin-bottom:var(--spacing-lg);">Parámetros del Crédito</h3>
                    
                    <div class="form-group calc-range">
                        <div class="calc-range__header">
                            <span>Valor total del Inmueble</span>
                            <span id="lbl-calc-price">$450,000</span>
                        </div>
                        <input type="range" min="50000" max="2000000" step="10000" value="450000" id="input-calc-price" oninput="calculateMortgage()">
                    </div>

                    <div class="form-group calc-range">
                        <div class="calc-range__header">
                            <span>Enganche / Cuota Inicial (%)</span>
                            <span id="lbl-calc-down">20% ($90,000)</span>
                        </div>
                        <input type="range" min="5" max="50" step="1" value="20" id="input-calc-down" oninput="calculateMortgage()">
                    </div>

                    <div class="form-group calc-range">
                        <div class="calc-range__header">
                            <span>Plazo del Préstamo (Años)</span>
                            <span id="lbl-calc-years">20 Años</span>
                        </div>
                        <input type="range" min="5" max="30" step="5" value="20" id="input-calc-years" oninput="calculateMortgage()">
                    </div>

                    <div class="form-group calc-range">
                        <div class="calc-range__header">
                            <span>Tasa de Interés Anual (%)</span>
                            <span id="lbl-calc-rate">7.5%</span>
                        </div>
                        <input type="range" min="2" max="15" step="0.1" value="7.5" id="input-calc-rate" oninput="calculateMortgage()">
                    </div>
                </div>

                <div style="display:flex; flex-direction:column; gap:var(--spacing-lg);">
                    <div class="calc-result-box">
                        <div style="font-size:0.9rem; text-transform:uppercase; letter-spacing:1px;">Pago Mensual Estimado</div>
                        <div class="calc-result-box__price" id="calc-monthly-payment">$2,900</div>
                        <p style="font-size:0.85rem; opacity:0.9;">Incluye capital e intereses. No incluye impuestos locales ni seguros.</p>
                    </div>

                    <div class="card">
                        <h4 style="margin-bottom:var(--spacing-md);">Desglose del Crédito</h4>
                        <div style="display:flex; justify-content:space-between; margin-bottom:8px; font-size:0.9rem;">
                            <span>Monto Total Financiado:</span>
                            <strong id="calc-loan-amount">$360,000</strong>
                        </div>
                        <div style="display:flex; justify-content:space-between; margin-bottom:8px; font-size:0.9rem;">
                            <span>Total de Intereses a pagar:</span>
                            <strong id="calc-total-interest" style="color:var(--color-secondary);">$336,000</strong>
                        </div>
                        <div style="display:flex; justify-content:space-between; font-size:0.9rem;">
                            <span>Costo Total del Inmueble:</span>
                            <strong id="calc-total-cost">$696,000</strong>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- PAGE 5: AGENDAR VISITA -->
        <section id="view-visit" class="view">
            <div class="view-header">
                <h1 class="view-header__title">Agendar Visita Guiada</h1>
                <p class="view-header__subtitle">Coordina una cita presencial o virtual directamente con el agente encargado</p>
            </div>

            <div class="card" style="max-width:700px; margin:0 auto;">
                <form onsubmit="handleScheduleVisit(event)">
                    <div class="form-group">
                        <label class="form-label">Selecciona el Inmueble a Visitar</label>
                        <select id="visit-property-select" class="form-select" required></select>
                    </div>
                    <div class="grid-2">
                        <div class="form-group">
                            <label class="form-label">Fecha Preferida</label>
                            <input type="date" class="form-input" required min="2026-08-28">
                        </div>
                        <div class="form-group">
                            <label class="form-label">Horario</label>
                            <select class="form-select" required>
                                <option value="10:00">10:00 AM</option>
                                <option value="12:00">12:00 PM</option>
                                <option value="16:00">04:00 PM</option>
                            </select>
                        </div>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Tu Nombre Completo</label>
                        <input type="text" class="form-input" required placeholder="Ej: Carlos Mendoza">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Teléfono de Contacto</label>
                        <input type="tel" class="form-input" required placeholder="+52 55 1234 5678">
                    </div>
                    <button type="submit" class="btn" style="width:100%;">Confirmar Cita de Visita</button>
                </form>
            </div>
        </section>

        <!-- PAGE 6: PUBLICAR PROPIEDAD (Multi-Step Form) -->
        <section id="view-publish" class="view">
            <div class="view-header">
                <h1 class="view-header__title">Publicar Inmueble en el Portal</h1>
                <p class="view-header__subtitle">Llega a miles de compradores e inversionistas calificados</p>
            </div>

            <div class="card" style="max-width:800px; margin:0 auto;">
                <div style="display:flex; justify-content:space-between; margin-bottom:var(--spacing-xl); border-bottom:1px solid var(--color-border); padding-bottom:var(--spacing-md);">
                    <span id="step-lbl-1" style="font-weight:700; color:var(--color-primary);">Paso 1: Información Básica</span>
                    <span id="step-lbl-2" style="color:var(--color-text-muted);">Paso 2: Detalles y Precio</span>
                </div>

                <form id="publish-form" onsubmit="handlePublishSubmit(event)">
                    <!-- Step 1 -->
                    <div id="publish-step-1">
                        <div class="form-group">
                            <label class="form-label">Título de la Publicación</label>
                            <input type="text" id="pub-title" class="form-input" required placeholder="Ej: Residencia Moderna con Alberca">
                        </div>
                        <div class="grid-2">
                            <div class="form-group">
                                <label class="form-label">Ubicación / Ciudad</label>
                                <input type="text" id="pub-location" class="form-input" required placeholder="Ej: Polanco, CDMX">
                            </div>
                            <div class="form-group">
                                <label class="form-label">Tipo de Inmueble</label>
                                <select id="pub-type" class="form-select">
                                    <option value="Casa">Casa</option>
                                    <option value="Departamento">Departamento</option>
                                    <option value="Villa">Villa</option>
                                </select>
                            </div>
                        </div>
                        <button type="button" class="btn btn--secondary" onclick="goToPublishStep(2)">Siguiente: Detalles →</button>
                    </div>

                    <!-- Step 2 -->
                    <div id="publish-step-2" style="display:none;">
                        <div class="grid-3">
                            <div class="form-group">
                                <label class="form-label">Precio ($ USD)</label>
                                <input type="number" id="pub-price" class="form-input" required placeholder="450000">
                            </div>
                            <div class="form-group">
                                <label class="form-label">Habitaciones</label>
                                <input type="number" id="pub-beds" class="form-input" required value="3">
                            </div>
                            <div class="form-group">
                                <label class="form-label">Baños</label>
                                <input type="number" id="pub-baths" class="form-input" required value="2">
                            </div>
                        </div>
                        <div class="form-group">
                            <label class="form-label">URL de Imagen Principal</label>
                            <input type="url" id="pub-img" class="form-input" required value="https://images.unsplash.com/photo-1600585154340-be6161a56a0c?auto=format&fit=crop&w=800&q=80">
                        </div>
                        <div style="display:flex; gap:12px;">
                            <button type="button" class="btn btn--outline" onclick="goToPublishStep(1)">← Volver</button>
                            <button type="submit" class="btn">Publicar Inmueble Ahora</button>
                        </div>
                    </div>
                </form>
            </div>
        </section>

        <!-- PAGE 7: DIRECTORIO DE AGENTES -->
        <section id="view-agents" class="view">
            <div class="view-header">
                <h1 class="view-header__title">Directorio de Agentes Inmobiliarios</h1>
                <p class="view-header__subtitle">Asesores certificados listos para guiar tu proceso de inversión</p>
            </div>

            <div class="grid-3">
                <div class="card" style="text-align:center;">
                    <img src="https://images.unsplash.com/photo-1560250097-0b93528c311a?auto=format&fit=crop&w=300&q=80" style="width:100px; height:100px; border-radius:50%; object-fit:cover; margin:0 auto 16px auto;" alt="Agente Sofia Martinez">
                    <h3>Lic. Sofía Martínez</h3>
                    <p style="color:var(--color-text-muted); font-size:0.85rem; margin-bottom:12px;">Especialista en Residencial de Lujo</p>
                    <div style="color:var(--color-secondary); font-weight:700; margin-bottom:16px;">★ 4.9 / 5.0 (48 Ventas)</div>
                    <button class="btn btn--outline" onclick="showToast('Contactando a Lic. Sofía Martínez...')">Contactar Agente</button>
                </div>

                <div class="card" style="text-align:center;">
                    <img src="https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?auto=format&fit=crop&w=300&q=80" style="width:100px; height:100px; border-radius:50%; object-fit:cover; margin:0 auto 16px auto;" alt="Agente Elena Gomez">
                    <h3>Ing. Elena Gómez</h3>
                    <p style="color:var(--color-text-muted); font-size:0.85rem; margin-bottom:12px;">Asesora de Inversiones Corporativas</p>
                    <div style="color:var(--color-secondary); font-weight:700; margin-bottom:16px;">★ 4.8 / 5.0 (62 Ventas)</div>
                    <button class="btn btn--outline" onclick="showToast('Contactando a Ing. Elena Gómez...')">Contactar Agente</button>
                </div>

                <div class="card" style="text-align:center;">
                    <img src="https://images.unsplash.com/photo-1519085360753-af0119f7cbe7?auto=format&fit=crop&w=300&q=80" style="width:100px; height:100px; border-radius:50%; object-fit:cover; margin:0 auto 16px auto;" alt="Agente Javier Rios">
                    <h3>Arq. Javier Ríos</h3>
                    <p style="color:var(--color-text-muted); font-size:0.85rem; margin-bottom:12px;">Desarrollos Urbanos y Terrenos</p>
                    <div style="color:var(--color-secondary); font-weight:700; margin-bottom:16px;">★ 5.0 / 5.0 (35 Ventas)</div>
                    <button class="btn btn--outline" onclick="showToast('Contactando a Arq. Javier Ríos...')">Contactar Agente</button>
                </div>
            </div>
        </section>

        <!-- PAGE 8: PORTAL DEL PROPIETARIO -->
        <section id="view-portal" class="view">
            <div class="view-header">
                <h1 class="view-header__title">Portal del Propietario / Vendedor</h1>
                <p class="view-header__subtitle">Métricas de rendimiento y visitas recibidas en tus publicaciones</p>
            </div>

            <div class="grid-3" style="margin-bottom:var(--spacing-xl);">
                <div class="card">
                    <span style="font-size:0.85rem; color:var(--color-text-muted);">Visualizaciones Totales</span>
                    <h2 style="font-size:2.2rem; color:var(--color-primary);">1,420</h2>
                    <span style="color:var(--color-status-available); font-weight:700; font-size:0.8rem;">▲ +18% este mes</span>
                </div>
                <div class="card">
                    <span style="font-size:0.85rem; color:var(--color-text-muted);">Prospectos Interesados</span>
                    <h2 style="font-size:2.2rem; color:var(--color-secondary);">28</h2>
                    <span style="color:var(--color-status-available); font-weight:700; font-size:0.8rem;">▲ 5 visitas agendadas</span>
                </div>
                <div class="card">
                    <span style="font-size:0.85rem; color:var(--color-text-muted);">Estado de Publicaciones</span>
                    <h2 style="font-size:2.2rem; color:var(--color-primary);">2 Activas</h2>
                    <span style="font-size:0.8rem; color:var(--color-text-muted);">Revisadas hoy</span>
                </div>
            </div>

            <div class="card">
                <h3 style="margin-bottom:var(--spacing-md);">Solicitudes de Contacto Recientes</h3>
                <table style="width:100%; border-collapse:collapse; font-size:0.9rem;">
                    <thead>
                        <tr style="border-bottom:2px solid var(--color-border); text-align:left;">
                            <th style="padding:10px;">Cliente</th>
                            <th style="padding:10px;">Inmueble</th>
                            <th style="padding:10px;">Fecha</th>
                            <th style="padding:10px;">Acción</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr style="border-bottom:1px solid var(--color-border);">
                            <td style="padding:10px;">Miguel Ángel Soto</td>
                            <td style="padding:10px;">Villa Contemporánea Polanco</td>
                            <td style="padding:10px;">27 Ago 2026</td>
                            <td style="padding:10px;"><button class="btn btn--outline" style="padding:4px 8px; font-size:0.75rem;" onclick="showToast('Abriendo chat con cliente...')">Responder</button></td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </section>

        <!-- PAGE 9: FAVORITOS (localStorage) -->
        <section id="view-favorites" class="view">
            <div class="view-header">
                <h1 class="view-header__title">Tus Propiedades Guardadas</h1>
                <p class="view-header__subtitle">Lista personalizada de casas almacenadas en tu navegador</p>
            </div>

            <div id="favorites-grid" class="grid-3"></div>
        </section>

        <!-- PAGE 10: CONTACTO Y OFICINAS -->
        <section id="view-contact" class="view">
            <div class="view-header">
                <h1 class="view-header__title">Contacto y Oficinas Corporativas</h1>
                <p class="view-header__subtitle">Estamos listos para escucharte y resolver tus dudas inmobiliarias</p>
            </div>

            <div class="grid-2">
                <div class="card">
                    <h3 style="margin-bottom:var(--spacing-md);">Envíanos un Mensaje</h3>
                    <form onsubmit="handleContactSubmit(event)">
                        <div class="form-group">
                            <label class="form-label">Nombre</label>
                            <input type="text" class="form-input" required placeholder="Tu nombre...">
                        </div>
                        <div class="form-group">
                            <label class="form-label">Correo Electrónico</label>
                            <input type="email" class="form-input" required placeholder="correo@ejemplo.com">
                        </div>
                        <div class="form-group">
                            <label class="form-label">Mensaje</label>
                            <textarea class="form-textarea" rows="4" required placeholder="¿En qué podemos ayudarte?"></textarea>
                        </div>
                        <button type="submit" class="btn">Enviar Formulario</button>
                    </form>
                </div>

                <div class="card">
                    <h3 style="margin-bottom:var(--spacing-md);">Nuestras Sucursales</h3>
                    <div style="margin-bottom:16px;">
                        <strong>Sede Central CDMX:</strong>
                        <p style="font-size:0.85rem; color:var(--color-text-muted);">Av. Paseo de la Reforma 405, Cuauhtémoc, CDMX.</p>
                    </div>
                    <div style="margin-bottom:16px;">
                        <strong>Oficina Monterrey:</strong>
                        <p style="font-size:0.85rem; color:var(--color-text-muted);">Av. San Pedro 200, San Pedro Garza García, NL.</p>
                    </div>
                    <div>
                        <strong>Horario de Atención:</strong>
                        <p style="font-size:0.85rem; color:var(--color-text-muted);">Lunes a Viernes: 09:00 AM - 07:00 PM | Sábados: 10:00 AM - 02:00 PM</p>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- FOOTER -->
    <footer class="footer">
        <div class="footer__container">
            <div>
                <h3 class="footer__title">HabitatPrime Real Estate</h3>
                <p style="font-size:0.85rem; opacity:0.8; max-width:320px;">Plataforma líder en comercialización y analítica de desarrollo inmobiliario con estándares WCAG 2.1 AA.</p>
            </div>
            <div>
                <h4 class="footer__title">Navegación</h4>
                <ul class="footer__list">
                    <li><a href="#" onclick="navigateTo('search')">Buscador</a></li>
                    <li><a href="#" onclick="navigateTo('listings')">Inmuebles</a></li>
                    <li><a href="#" onclick="navigateTo('mortgage')">Calculadora</a></li>
                </ul>
            </div>
            <div>
                <h4 class="footer__title">Legal</h4>
                <ul class="footer__list">
                    <li>Términos de Servicio</li>
                    <li>Aviso de Privacidad</li>
                    <li>Licencia Inmobiliaria</li>
                </ul>
            </div>
            <div>
                <h4 class="footer__title">Soporte</h4>
                <ul class="footer__list">
                    <li>contacto@habitatprime.com</li>
                    <li>+52 (55) 8000-9000</li>
                </ul>
            </div>
        </div>
        <div class="footer__bottom">
            &copy; 2026 HabitatPrime Platform. Todos los derechos reservados.
        </div>
    </footer>

    <!-- CONTAINER PARA TOASTS -->
    <div id="toast-container" class="toast-container"></div>

    <!-- ==========================================================================
       5. JAV
