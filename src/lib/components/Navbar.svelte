<script>
  import { page } from '$app/stores';
  import { afterNavigate } from '$app/navigation';
  import { onMount } from 'svelte';
  import MobileMenu from './MobileMenu.svelte';

  let menuOpen = false;
  let scrolled = false;
  let io = null;

  const links = [
    { href: '/about',    label: 'About' },
    { href: '/menu',     label: 'Menu' },
    { href: '/catering', label: 'Catering' },
    { href: '/contact',  label: 'Contact' },
  ];

  // Menu page has no dark hero — always solid
  $: alwaysSolid = $page.url.pathname === '/menu';
  $: navSolid = alwaysSolid || scrolled;

  function setupObserver() {
    if (io) { io.disconnect(); io = null; }
    scrolled = false;

    if (window.location.pathname === '/menu') return;

    const hero = document.querySelector('section');
    if (!hero) return;

    io = new IntersectionObserver(
      ([entry]) => { scrolled = !entry.isIntersecting; },
      { threshold: 0 }
    );
    io.observe(hero);
  }

  onMount(() => {
    setupObserver();
    return () => { if (io) io.disconnect(); };
  });

  afterNavigate(setupObserver);
</script>

<header class="navbar" class:solid={navSolid}>
  <div class="nav-inner">

    <!-- Left: all nav links -->
    <nav class="nav-left desktop-nav" aria-label="Main navigation">
      {#each links as { href, label }}
        <a {href} class="nav-link" class:active={$page.url.pathname === href}>{label}</a>
      {/each}
    </nav>

    <!-- Center: logo -->
    <a href="/" class="logo-link" aria-label="Seaside Paradise Home">
      <img src="/logo-navbar.svg" alt="Seaside Paradise Restaurant" class="logo" />
    </a>

    <!-- Right: Phone + CTA -->
    <div class="nav-right">
      <a href="tel:+13455164367" class="phone">+1 (345) 516-4367</a>
      <div class="nav-divider"></div>
      <a href="/menu" class="nav-cta">View Menu</a>
    </div>

    <!-- Mobile Hamburger -->
    <button
      class="hamburger"
      aria-label="Open menu"
      aria-expanded={menuOpen}
      on:click={() => menuOpen = true}
    >
      <span></span><span></span><span></span>
    </button>

  </div>
</header>

<MobileMenu {links} bind:open={menuOpen} />

<style>
  .navbar {
    position: sticky;
    top: 0;
    z-index: 100;
    height: var(--navbar-h);
    /* Dark scrim gradient for text readability over hero photos */
    background: linear-gradient(to bottom, rgba(0,0,0,0.52) 0%, rgba(0,0,0,0) 100%);
    border-bottom: 1px solid transparent;
    transition: background 0.35s ease, border-color 0.35s ease, box-shadow 0.35s ease;
  }

  .navbar.solid {
    background: #fffff4;
    border-bottom-color: rgba(45,26,20,0.1);
    box-shadow: 0 2px 20px rgba(0,0,0,0.08);
  }
  .navbar.solid .nav-link { color: var(--dark); }
  .navbar.solid .phone { color: var(--dark); }
  .navbar.solid .nav-divider { background: rgba(45,26,20,0.2); }
  .navbar.solid .hamburger span { background: var(--dark); }

  .nav-inner {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    align-items: center;
    height: 100%;
    max-width: var(--container);
    margin: 0 auto;
    padding: 0 clamp(20px, 5.6vw, 80px);
  }

  /* ── Left: nav links ── */
  .nav-left {
    display: flex;
    align-items: center;
    gap: 36px;
    justify-content: flex-start;
  }

  /* ── Center: logo ── */
  .logo-link {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }
  .logo {
    height: 84px;
    width: auto;
    max-width: 300px;
  }

  .desktop-nav {
    display: flex;
    align-items: center;
    gap: 36px;
  }

  .nav-link {
    font-family: var(--font-body);
    font-size: 15px;
    color: var(--cream);
    opacity: 0.88;
    white-space: nowrap;
    transition: opacity 0.2s;
  }
  .nav-link:hover,
  .nav-link.active { opacity: 1; }

  /* ── Right: Phone + Divider + CTA ── */
  .nav-right {
    display: flex;
    align-items: center;
    height: 100%;
    gap: 24px;
    justify-content: flex-end;
    flex-shrink: 0;
  }

  .phone {
    font-family: var(--font-body);
    font-size: 14px;
    color: var(--cream);
    opacity: 0.8;
    white-space: nowrap;
    transition: opacity 0.2s;
  }
  .phone:hover { opacity: 1; }

  .nav-divider {
    width: 1px;
    height: 28px;
    background: rgba(232, 151, 58, 0.4);
    flex-shrink: 0;
  }

  /* Full-height CTA */
  .nav-cta {
    display: flex;
    align-items: center;
    justify-content: center;
    align-self: stretch;
    padding: 0 22px;
    background: var(--red);
    color: #fff8ee;
    font-family: var(--font-body);
    font-weight: 600;
    font-size: 13px;
    white-space: nowrap;
    border-radius: 3px;
    transition: opacity 0.2s;
  }
  .nav-cta:hover { opacity: 0.88; }

  /* ── Mobile ── */
  .hamburger {
    display: none;
    flex-direction: column;
    gap: 4px;
    align-items: flex-end;
    width: 100px;
    cursor: pointer;
    border: none;
    background: none;
    padding: 0;
  }
  .hamburger span {
    display: block;
    width: 22px;
    height: 2px;
    border-radius: 1px;
    background: var(--cream);
    transition: 0.3s;
  }
  .hamburger span:nth-child(2) { width: 18px; }

  @media (max-width: 900px) {
    .navbar {
      height: var(--navbar-h-mobile);
      border-bottom: none;
      box-shadow: none;
    }
    .navbar.solid {
      border-bottom: none;
      box-shadow: none;
    }
    .nav-inner {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0 24px;
      height: 100%;
    }
    .logo { height: 60px; max-width: 220px; }
    .nav-left,
    .nav-right { display: none; }
    .hamburger { display: flex; }
  }
</style>
