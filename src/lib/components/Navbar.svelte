<script>
  import { page } from '$app/stores';
  import MobileMenu from './MobileMenu.svelte';

  let menuOpen = false;
  const links = [
    { href: '/about',   label: 'About' },
    { href: '/menu',    label: 'Menu' },
    { href: '/catering', label: 'Catering' },
    { href: '/contact', label: 'Contact' },
  ];
</script>

<header class="navbar">
  <div class="nav-inner">
    <!-- Logo -->
    <a href="/" class="logo-link" aria-label="Seaside Paradise Home">
      <img src="/logo.svg" alt="Seaside Paradise Restaurant" class="logo" />
    </a>

    <!-- Desktop Nav Links -->
    <nav class="desktop-nav" aria-label="Main navigation">
      {#each links as { href, label }}
        <a {href} class="nav-link" class:active={$page.url.pathname === href}>{label}</a>
      {/each}
    </nav>

    <!-- Desktop Right -->
    <div class="nav-right">
      <a href="tel:+13455164367" class="phone">+1 (345) 516-4367</a>
      <div class="nav-divider"></div>
      <a href="/menu" class="btn btn-red nav-cta">View Menu</a>
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
    background: var(--bg-dark);
    height: var(--navbar-h);
    border-bottom: 1px solid rgba(255,255,255,0.06);
  }

  .nav-inner {
    display: flex;
    align-items: center;
    height: 100%;
    max-width: var(--container);
    margin: 0 auto;
    padding: 0 clamp(20px, 5vw, 60px);
    gap: 40px;
  }

  .logo-link { flex-shrink: 0; display: flex; align-items: center; }
  .logo { height: 44px; width: auto; }

  .desktop-nav {
    display: flex;
    gap: 32px;
    flex: 1;
  }

  .nav-link {
    font-family: var(--font-body);
    font-size: 15px;
    color: var(--cream);
    opacity: 0.8;
    transition: opacity 0.2s;
    white-space: nowrap;
  }
  .nav-link:hover, .nav-link.active { opacity: 1; }

  .nav-right {
    display: flex;
    align-items: center;
    gap: 20px;
    margin-left: auto;
    flex-shrink: 0;
  }

  .phone {
    font-size: 14px;
    color: var(--cream);
    opacity: 0.75;
    white-space: nowrap;
  }
  .phone:hover { opacity: 1; }

  .nav-divider {
    width: 1px;
    height: 28px;
    background: var(--amber);
    opacity: 0.5;
  }

  .nav-cta {
    padding: 10px 20px;
    font-size: 13px;
  }

  .hamburger {
    display: none;
    flex-direction: column;
    gap: 5px;
    padding: 8px;
    margin-left: auto;
  }
  .hamburger span {
    display: block;
    width: 22px;
    height: 2px;
    background: var(--cream);
    transition: 0.3s;
  }
  .hamburger span:nth-child(2) { width: 16px; }

  @media (max-width: 900px) {
    .desktop-nav, .nav-right { display: none; }
    .hamburger { display: flex; }
    .nav-inner { gap: 0; }
  }
</style>
