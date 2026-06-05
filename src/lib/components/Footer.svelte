<script>
  const year = new Date().getFullYear();
</script>

<footer class="footer">
  <div class="container">
    <!-- Top Row -->
    <div class="footer-grid">
      <div class="col-links">
        <p class="col-title">Links</p>
        <nav>
          <a href="/">Home</a>
          <a href="/about">About</a>
          <a href="/catering">Services</a>
          <a href="/catering">Catering</a>
        </nav>
      </div>

      <div class="col-menu">
        <p class="col-title">Menu</p>
        <nav>
          <a href="/menu">Monday</a>
          <a href="/menu">Tuesday</a>
          <a href="/menu">Wednesday</a>
          <a href="/menu">Thursday</a>
          <a href="/menu">Friday</a>
          <a href="/menu">Sat &amp; Sun</a>
        </nav>
      </div>

      <div class="col-address">
        <p class="col-title">Address</p>
        <p>166 Bodden Town Road,<br />Bodden Town, Grand Cayman,<br />KY2-2500</p>
        <a href="tel:+13455164367" class="phone">+1 (345) 516-4367</a>
        <a href="https://maps.google.com/?q=Seaside+Paradise+Restaurant+Bodden+Town" target="_blank" rel="noopener" class="map-link">Get location direction</a>
      </div>

      <div class="col-brand">
        <p class="about-text">At Seaside Paradise, we serve fresh local and Caribbean dishes every day. Part of the Rodneys Group, right here in Bodden Town.</p>
        <a href="/" aria-label="Seaside Paradise Home">
          <img src="/logo.svg" alt="Seaside Paradise Restaurant" class="footer-logo" />
        </a>
        <div class="hours-block">
          <p class="col-title">Hours</p>
          <p>Mon – Sun: 11:00 AM – 10:30 PM</p>
          <p class="open-tag">Open every day</p>
        </div>
      </div>
    </div>

    <!-- Bottom Bar -->
    <div class="footer-bottom">
      <p>Copyright &copy; Rodneys Group Ltd. All rights reserved.</p>
      <div class="footer-legal">
        <a href="/privacy">Privacy Policy</a>
        <a href="/terms">Terms &amp; Conditions</a>
      </div>
    </div>
  </div>
</footer>

<style>
  .footer {
    background: var(--footer-dark);
    color: var(--cream);
    padding-top: 64px;
  }

  .footer-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1.5fr 2fr;
    gap: 40px;
    padding-bottom: 48px;
    border-bottom: 1px solid rgba(255,255,255,0.08);
  }

  .col-title {
    font-family: var(--font-label);
    font-weight: 600;
    font-size: 15px;
    color: var(--cream);
    margin-bottom: 16px;
  }

  nav { display: flex; flex-direction: column; gap: 10px; }
  nav a {
    font-size: 14px;
    color: rgba(247,240,220,0.65);
    transition: color 0.2s;
  }
  nav a:hover { color: var(--amber); }

  .col-address p { font-size: 14px; color: rgba(247,240,220,0.65); line-height: 1.7; }
  .phone {
    display: block;
    margin-top: 12px;
    font-size: 14px;
    color: rgba(247,240,220,0.65);
    transition: color 0.2s;
  }
  .phone:hover { color: var(--amber); }
  .map-link {
    display: block;
    margin-top: 8px;
    font-size: 13px;
    font-weight: 600;
    color: var(--cream);
    text-decoration: underline;
    text-underline-offset: 3px;
    opacity: 0.7;
    transition: opacity 0.2s;
  }
  .map-link:hover { opacity: 1; }

  .col-brand {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }
  .about-text {
    font-size: 14px;
    color: rgba(247,240,220,0.6);
    line-height: 1.7;
  }
  .footer-logo { height: 36px; width: auto; }

  .hours-block { margin-top: 4px; }
  .hours-block p { font-size: 14px; color: rgba(247,240,220,0.65); }
  .open-tag { color: var(--amber) !important; font-size: 13px !important; margin-top: 2px; }

  .footer-bottom {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 0;
    font-size: 13px;
    color: rgba(247,240,220,0.4);
    flex-wrap: wrap;
    gap: 12px;
  }
  .footer-legal { display: flex; gap: 24px; }
  .footer-legal a { color: rgba(247,240,220,0.4); transition: color 0.2s; }
  .footer-legal a:hover { color: var(--cream); }

  @media (max-width: 900px) {
    .footer-grid {
      grid-template-columns: 1fr 1fr;
    }
    .col-address { grid-column: 1; }
    .col-brand { grid-column: 2; }
  }

  @media (max-width: 600px) {
    .footer-grid {
      grid-template-columns: 1fr 1fr;
      gap: 32px;
    }
    .col-address, .col-brand { grid-column: 1 / -1; }
    .footer-bottom { flex-direction: column; align-items: flex-start; }
  }
</style>
