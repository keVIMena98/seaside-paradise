<footer class="footer">
  <div class="footer-inner">

    <!-- ── Main content ── -->
    <div class="footer-content">

      <!-- Left group: Links · Menu · Address -->
      <div class="footer-left">

        <div class="footer-col">
          <p class="col-heading">Links</p>
          <nav class="col-items">
            <a href="/">Home</a>
            <a href="/about">About</a>
            <a href="/menu">Menu</a>
            <a href="/catering">Catering</a>
            <a href="/contact">Contact</a>
          </nav>
        </div>

        <div class="footer-col">
          <p class="col-heading">Menu</p>
          <nav class="col-items">
            <a href="/menu">Monday</a>
            <a href="/menu">Tuesday</a>
            <a href="/menu">Wednesday</a>
            <a href="/menu">Thursday</a>
            <a href="/menu">Friday</a>
            <a href="/menu">Sat &amp; Sun</a>
          </nav>
        </div>

        <div class="footer-col col-address">
          <p class="col-heading">Address</p>
          <div class="address-content">
            <div class="address-text">
              <p>238 Bodden Town Road,<br />Bodden Town, Grand Cayman,<br />KY2-2500</p>
              <p>+1 (345) 516-4367</p>
            </div>
            <a
              href="https://maps.google.com/?q=Seaside+Paradise+Restaurant+Bodden+Town"
              target="_blank"
              rel="noopener"
              class="map-link"
            >Get location direction</a>
          </div>
        </div>

      </div>

      <!-- Right group: About · Logo · Hours -->
      <div class="footer-right">

        <div class="company-block">
          <p class="about-text">At Seaside Paradise, we serve fresh local and Caribbean dishes every day. Part of the Rodneys Group, right here in Bodden Town.</p>
          <a href="/" aria-label="Seaside Paradise Home">
            <img src="/logo.png" alt="Seaside Paradise Restaurant" class="footer-logo" />
          </a>
        </div>

        <div class="hours-block">
          <p class="col-heading">Hours</p>
          <div class="hours-text">
            <p>Mon – Sun: 11:00 AM – 9:30 PM</p>
            <p>Open every day</p>
          </div>
        </div>

      </div>
    </div>

    <!-- ── Copyright bar ── -->
    <div class="footer-bottom">
      <p>Copyright &copy; Rodneys Group Ltd. All rights reserved.</p>
      <div class="footer-legal">
        <a href="https://www.sparkframelabs.com" class="credit-link" target="_blank" rel="noopener noreferrer">Credit</a>
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
  }

  .footer-inner {
    max-width: var(--container);
    margin: 0 auto;
    padding: 72px clamp(20px, 5.6vw, 80px) 40px;
    display: flex;
    flex-direction: column;
    gap: 120px;
  }

  /* ── Main content row ── */
  .footer-content {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    padding-top: 16px;
    gap: 40px;
  }

  /* ── Left group ── */
  .footer-left {
    display: flex;
    justify-content: space-between;
    gap: 40px;
    flex: 0 0 auto;
    width: min(758px, 58%);
  }

  .footer-col {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .col-heading {
    font-family: var(--font-label);
    font-weight: 600;
    font-size: 26px;
    line-height: 32px;
    color: var(--cream);
    white-space: nowrap;
  }

  .col-items {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .col-items a {
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 24px;
    color: var(--cream);
    opacity: 0.8;
    white-space: nowrap;
    transition: opacity 0.2s;
  }
  .col-items a:hover { opacity: 1; }

  /* ── Address column ── */
  .col-address { width: 252px; flex-shrink: 0; }

  .address-content {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    min-height: 204px;
    gap: 24px;
  }

  .address-text {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .address-text p {
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 24px;
    color: var(--cream);
    opacity: 0.8;
  }

  .map-link {
    display: inline-block;
    font-family: var(--font-body);
    font-weight: 600;
    font-size: 16px;
    line-height: 24px;
    color: var(--cream);
    opacity: 0.8;
    border-bottom: 1px solid var(--cream);
    padding-bottom: 4px;
    transition: opacity 0.2s;
    align-self: flex-start;
  }
  .map-link:hover { opacity: 1; }

  /* ── Right group ── */
  .footer-right {
    display: flex;
    flex-direction: column;
    gap: 41px;
    flex-shrink: 0;
    max-width: 413px;
  }

  .company-block {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .about-text {
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 24px;
    color: var(--cream);
    opacity: 0.8;
  }

  .footer-logo {
    height: 56px;
    width: auto;
    max-width: 200px;
    display: block;
  }

  .hours-block {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .hours-text {
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 24px;
    color: var(--cream);
    opacity: 0.8;
  }

  /* ── Copyright bar ── */
  .footer-bottom {
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 24px;
    color: var(--cream);
    flex-wrap: wrap;
    gap: 16px;
  }

  .footer-bottom > p,
  .footer-legal a {
    opacity: 0.5;
  }

  .footer-legal {
    display: flex;
    gap: 40px;
    align-items: center;
  }

  .footer-legal a {
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 24px;
    color: var(--cream);
    white-space: nowrap;
    transition: opacity 0.2s;
  }
  .footer-legal a:hover { opacity: 0.8; }

  /* ── Responsive ── */
  @media (max-width: 1100px) {
    .footer-left { width: auto; flex: 1; }
    .footer-right { max-width: 320px; }
  }

  @media (max-width: 900px) {
    .footer-inner { gap: 72px; }
    .footer-content { flex-direction: column; gap: 48px; }
    .footer-left { width: 100%; }
    .footer-right { max-width: 100%; }
  }

  /* ── Mobile (matches Figma 390px spec) ── */
  @media (max-width: 600px) {
    /* Container */
    .footer-inner {
      padding: 56px 24px 40px;
      gap: 40px;
    }
    .footer-content { gap: 40px; }

    /* Links + Menu side-by-side, Address wraps to full-width row below */
    .footer-left {
      flex-wrap: wrap;
      gap: 40px;
    }
    .col-address {
      flex: 0 0 100%;
      width: 100%;
    }
    .address-content { min-height: unset; }

    /* Headings: 20px on mobile */
    .col-heading { font-size: 20px; line-height: normal; }

    /* Items: full opacity on mobile */
    .col-items a { opacity: 1; }
    .address-text p { opacity: 1; }
    .about-text { opacity: 1; }
    .hours-text { opacity: 1; }

    /* "Get location direction": bold text, no border on mobile */
    .map-link {
      border-bottom: none;
      padding-bottom: 0;
      opacity: 1;
    }

    /* Logo: 120×33 on mobile */
    .footer-logo { height: 33px; max-width: 120px; }

    /* Brand+Hours block: tighter gaps */
    .footer-right { gap: 16px; }
    .company-block { gap: 16px; }

    /* Copyright: centered, 14px, 0.6 opacity, stacked */
    .footer-bottom {
      flex-direction: column;
      align-items: center;
      text-align: center;
      gap: 8px;
      font-size: 14px;
    }
    .footer-bottom > p { opacity: 0.6; font-size: 14px; }
    .footer-legal { gap: 24px; }
    .footer-legal a { opacity: 0.6; font-size: 14px; }

    /* "Credit" is not shown in mobile Figma */
    .credit-link { display: none; }
  }
</style>
