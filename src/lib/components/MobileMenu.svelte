<script>
  export let open = false;
  export let links = [];
  import { page } from '$app/stores';

  const subtitles = {
    'About':    'About the restaurant',
    'Menu':     'See our daily menu',
    'Catering': 'Private events & catering',
    'Contact':  'Find us in Bodden Town',
  };

  function close() { open = false; }
</script>

{#if open}
  <div
    class="mobile-menu"
    role="dialog"
    aria-modal="true"
    aria-label="Mobile navigation"
  >
    <!-- Top bar -->
    <div class="topbar">
      <a href="/" class="logo-link" on:click={close} aria-label="Home">
        <img src="/logo.png" alt="Seaside Paradise" class="logo" />
      </a>
      <button class="close-btn" on:click={close} aria-label="Close menu">✕</button>
    </div>

    <div class="divider-line"></div>

    <!-- Nav links -->
    <nav class="nav-links" aria-label="Mobile navigation">
      {#each links as { href, label }}
        <a {href} class="nav-item" class:active={$page.url.pathname === href} on:click={close}>
          <span class="item-label">{label}</span>
          {#if subtitles[label]}
            <span class="item-sub">{subtitles[label]}</span>
          {/if}
          <div class="item-border"></div>
        </a>
      {/each}
    </nav>

    <!-- Contact details -->
    <div class="contact-block">
      <div class="phone-row">
        <span class="dot"></span>
        <a href="tel:+13455164367" class="phone-text" on:click={close}>+1 (345) 516-4367</a>
      </div>
      <p class="social-text">@seasideparadiserestaurant</p>
      <p class="social-text">@seasideparadisefood (TikTok)</p>
    </div>

    <!-- CTA -->
    <div class="cta-block">
      <a href="/menu" class="view-menu" on:click={close}>View Menu</a>
    </div>
  </div>
{/if}

<style>
  .mobile-menu {
    position: fixed;
    inset: 0;
    background: #1c1610;
    z-index: 200;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    overflow-y: auto;
    padding-bottom: 48px;
    animation: menuIn 0.28s cubic-bezier(0.4, 0, 0.2, 1);
  }

  @keyframes menuIn {
    from { opacity: 0; transform: translateX(16px); }
    to   { opacity: 1; transform: translateX(0); }
  }

  /* Top bar */
  .topbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 24px;
    height: 64px;
    flex-shrink: 0;
  }

  .logo { height: 33px; width: auto; max-width: 120px; display: block; }
  .logo-link { display: flex; align-items: center; }

  .close-btn {
    color: var(--cream);
    font-size: 20px;
    line-height: 1;
    padding: 8px;
    background: none;
    border: none;
    cursor: pointer;
    font-family: var(--font-body);
    display: flex;
    align-items: center;
    justify-content: center;
  }

  /* Divider */
  .divider-line {
    flex-shrink: 0;
    height: 1px;
    background: rgba(247, 240, 220, 0.15);
  }

  /* Nav links */
  .nav-links {
    display: flex;
    flex-direction: column;
    flex-shrink: 0;
  }

  .nav-item {
    position: relative;
    display: flex;
    flex-direction: column;
    gap: 4px;
    padding: 24px;
    min-height: 88px;
    text-decoration: none;
    transition: background 0.15s;
  }
  .nav-item:hover { background: rgba(255,255,255,0.04); }

  .item-label {
    font-family: var(--font-label);
    font-weight: 600;
    font-size: 40px;
    line-height: normal;
    color: var(--cream);
    white-space: nowrap;
  }
  .nav-item.active .item-label { color: var(--amber); }

  .item-sub {
    font-family: var(--font-body);
    font-size: 13px;
    line-height: normal;
    color: rgba(247, 240, 220, 0.45);
    letter-spacing: 0.52px;
    white-space: nowrap;
  }

  .item-border {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 1px;
    background: rgba(247, 240, 220, 0.1);
  }
  .nav-item:last-child .item-border { display: none; }

  /* Contact */
  .contact-block {
    display: flex;
    flex-direction: column;
    gap: 8px;
    padding: 32px 24px 0;
    flex-shrink: 0;
  }

  .phone-row {
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .dot {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: var(--amber);
    flex-shrink: 0;
  }

  .phone-text {
    font-family: var(--font-body);
    font-weight: 600;
    font-size: 15px;
    line-height: normal;
    color: var(--cream);
    text-decoration: none;
  }

  .social-text {
    font-family: var(--font-body);
    font-size: 13px;
    line-height: normal;
    color: rgba(247, 240, 220, 0.6);
  }

  /* CTA */
  .cta-block {
    padding: 24px;
    flex-shrink: 0;
  }

  .view-menu {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding: 16px;
    background: var(--red);
    color: var(--cream);
    font-family: var(--font-body);
    font-weight: 600;
    font-size: 16px;
    line-height: normal;
    text-decoration: none;
    transition: opacity 0.2s;
  }
  .view-menu:hover { opacity: 0.9; }
</style>
