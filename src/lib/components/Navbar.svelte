<script>
  import { page } from '$app/stores';
  import MobileMenu from './MobileMenu.svelte';

  let menuOpen = false;
  const links = [
    { href: '/about',    label: 'About' },
    { href: '/menu',     label: 'Menu' },
    { href: '/catering', label: 'Catering' },
    { href: '/contact',  label: 'Contact' },
  ];
</script>

<header class="navbar">
  <div class="nav-inner">

    <!-- Logo + Links -->
    <div class="nav-left">
      <a href="/" class="logo-link" aria-label="Seaside Paradise Home">
        <img src="/logo.png" alt="Seaside Paradise Restaurant" class="logo" />
      </a>
      <nav class="desktop-nav" aria-label="Main navigation">
        {#each links as { href, label }}
          <a {href} class="nav-link" class:active={$page.url.pathname === href}>{label}</a>
        {/each}
      </nav>
    </div>

    <!-- Phone + CTA -->
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
    border-bottom: 1px solid rgba(255,255,255,0.06);
  }

  .nav-inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 100%;
    max-width: var(--container);
    margin: 0 auto;
    padding: 0 clamp(20px, 5.6vw, 80px);
  }

  /* ── Left group: Logo + Nav Links ── */
  .nav-left {
    display: flex;
    align-items: center;
    gap: 52px;
    height: 100%;
  }

  .logo-link {
    display: flex;
    align-items: center;
    flex-shrink: 0;
  }
  .logo {
    height: 44px;
    width: auto;
    max-width: 160px;
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
    opacity: 0.8;
    white-space: nowrap;
    transition: opacity 0.2s;
  }
  .nav-link:hover,
  .nav-link.active { opacity: 1; }

  /* ── Right group: Phone + Divider + CTA ── */
  .nav-right {
    display: flex;
    align-items: center;
    height: 100%;
    gap: 24px;
    flex-shrink: 0;
  }

  .phone {
    font-family: var(--font-body);
    font-size: 14px;
    color: var(--cream);
    opacity: 0.75;
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

  /* Full-height CTA — matches Figma h-[100px] */
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
    transition: opacity 0.2s, background 0.2s;
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
    background: #222;
    transition: 0.3s;
  }
  .hamburger span:nth-child(2) { width: 18px; }

  @media (max-width: 900px) {
    .navbar {
      height: auto;
      border-bottom: none;
    }
    .nav-inner {
      padding: 16px 24px;
      height: auto;
    }
    .nav-left { gap: 0; }
    .logo { height: 33px; max-width: 120px; }
    .desktop-nav,
    .nav-right { display: none; }
    .hamburger { display: flex; }
  }
</style>
