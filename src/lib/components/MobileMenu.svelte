<script>
  export let open = false;
  export let links = [];
  import { page } from '$app/stores';

  function close() { open = false; }
</script>

{#if open}
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div class="overlay" on:click={close}></div>
{/if}

<nav class="mobile-menu" class:open aria-label="Mobile navigation" aria-hidden={!open}>
  <div class="menu-top">
    <a href="/" class="logo-link" on:click={close} aria-label="Home">
      <img src="/logo.svg" alt="Seaside Paradise Restaurant" class="logo" />
    </a>
    <button class="close-btn" on:click={close} aria-label="Close menu">
      <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
        <path d="M2 2L18 18M18 2L2 18" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
      </svg>
    </button>
  </div>

  <div class="menu-links">
    {#each links as { href, label }, i}
      <a
        {href}
        class="menu-item"
        class:active={$page.url.pathname === href}
        on:click={close}
        style="animation-delay: {i * 60}ms"
      >
        <span class="item-label">{label}</span>
        <svg class="arrow" width="16" height="16" viewBox="0 0 16 16" fill="none">
          <path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </a>
      <div class="divider"></div>
    {/each}
  </div>

  <div class="menu-footer">
    <a href="tel:+13455164367" class="footer-phone" on:click={close}>
      <span class="dot"></span>+1 (345) 516-4367
    </a>
    <p class="footer-social">@seasideparadiserestaurant</p>
    <p class="footer-social">@seasideparadisefood (TikTok)</p>
    <a href="/menu" class="btn btn-red view-menu" on:click={close}>View Menu</a>
  </div>
</nav>

<style>
  .overlay {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.6);
    z-index: 199;
    backdrop-filter: blur(2px);
  }

  .mobile-menu {
    position: fixed;
    top: 0;
    left: 0;
    width: min(340px, 90vw);
    height: 100dvh;
    background: var(--bg-dark);
    z-index: 200;
    display: flex;
    flex-direction: column;
    transform: translateX(-100%);
    transition: transform 0.35s cubic-bezier(0.4, 0, 0.2, 1);
    overflow-y: auto;
  }
  .mobile-menu.open { transform: translateX(0); }

  .menu-top {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 24px;
    border-bottom: 1px solid rgba(255,255,255,0.08);
    flex-shrink: 0;
  }
  .logo { height: 32px; width: auto; }

  .close-btn {
    color: var(--cream);
    padding: 6px;
    opacity: 0.7;
    transition: opacity 0.2s;
  }
  .close-btn:hover { opacity: 1; }

  .menu-links {
    flex: 1;
    padding: 24px 0;
  }

  .menu-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 24px;
    font-family: var(--font-label);
    font-weight: 600;
    font-size: 22px;
    color: var(--cream);
    opacity: 0.85;
    transition: opacity 0.2s, padding-left 0.2s;
  }
  .menu-item:hover, .menu-item.active {
    opacity: 1;
    padding-left: 28px;
    color: var(--amber);
  }
  .arrow { opacity: 0.5; flex-shrink: 0; }
  .menu-item:hover .arrow, .menu-item.active .arrow { opacity: 1; }

  .divider {
    height: 1px;
    background: rgba(255,255,255,0.06);
    margin: 0 24px;
  }

  .menu-footer {
    padding: 24px;
    border-top: 1px solid rgba(255,255,255,0.08);
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .footer-phone {
    display: flex;
    align-items: center;
    gap: 8px;
    color: var(--cream);
    font-size: 15px;
    font-weight: 600;
    margin-bottom: 4px;
  }
  .dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: var(--amber);
    flex-shrink: 0;
  }
  .footer-social {
    font-size: 13px;
    color: var(--cream);
    opacity: 0.55;
  }

  .view-menu {
    margin-top: 16px;
    width: 100%;
  }
</style>
