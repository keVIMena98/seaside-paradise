<svelte:head>
  <title>Privacy Policy — Seaside Paradise Restaurant</title>
</svelte:head>

<section class="legal-section">
  <div class="legal-inner">
    <div class="legal-header">
      <p class="eyebrow">LEGAL</p>
      <h1 class="legal-title">Privacy Policy</h1>
      <p class="legal-date">Last updated: June 2026</p>
    </div>

    <div class="legal-body">
      <div class="legal-block">
        <h2>1. Information We Collect</h2>
        <p>When you contact us through our website, we collect the information you provide: your name, phone number, email address, and message. We do not collect any payment information through this website.</p>
      </div>

      <div class="legal-block">
        <h2>2. How We Use Your Information</h2>
        <p>We use your contact information solely to respond to your enquiries, process catering or event requests, and send you information you have requested about Seaside Paradise Restaurant. We do not sell, trade, or transfer your personal information to third parties.</p>
      </div>

      <div class="legal-block">
        <h2>3. Data Storage</h2>
        <p>Contact form submissions are delivered to our email inbox and are retained only as long as necessary to respond to your enquiry. We do not maintain a separate database of contact records.</p>
      </div>

      <div class="legal-block">
        <h2>4. Cookies</h2>
        <p>This website does not use tracking cookies or analytics. We do not track your browsing behaviour across other sites.</p>
      </div>

      <div class="legal-block">
        <h2>5. Third-Party Services</h2>
        <p>Our contact form is processed through Formspree. Please refer to <a href="https://formspree.io/legal/privacy-policy" target="_blank" rel="noopener">Formspree's Privacy Policy</a> for information on how they handle form data.</p>
      </div>

      <div class="legal-block">
        <h2>6. Your Rights</h2>
        <p>You have the right to request access to, correction of, or deletion of any personal information we hold about you. To make such a request, please contact us at <a href="mailto:seasideparadiseky@gmail.com">seasideparadiseky@gmail.com</a>.</p>
      </div>

      <div class="legal-block">
        <h2>7. Contact</h2>
        <p>If you have any questions about this privacy policy, please contact us at:</p>
        <p>Seaside Paradise Restaurant<br />166 Bodden Town Road, Bodden Town, Grand Cayman, KY2-2500<br /><a href="mailto:seasideparadiseky@gmail.com">seasideparadiseky@gmail.com</a><br /><a href="tel:+13455164367">+1 (345) 516-4367</a></p>
      </div>
    </div>

    <div class="legal-back">
      <a href="/">&larr; Back to Home</a>
    </div>
  </div>
</section>

<style>
  .legal-section {
    background: #fffff4;
    padding: clamp(60px, 7vw, 100px) clamp(24px, 5.6vw, 80px);
    min-height: 60vh;
  }
  .legal-inner {
    max-width: 800px;
    margin: 0 auto;
  }
  .legal-header {
    margin-bottom: 56px;
    padding-bottom: 40px;
    border-bottom: 1px solid rgba(45,26,20,0.12);
  }
  .eyebrow {
    font-family: var(--font-label);
    font-weight: 600;
    font-size: 12px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--amber);
    margin-bottom: 12px;
  }
  .legal-title {
    font-family: var(--font-display);
    font-size: clamp(36px, 5vw, 64px);
    line-height: 1.1;
    color: var(--dark);
    margin-bottom: 12px;
  }
  .legal-date {
    font-family: var(--font-body);
    font-size: 14px;
    color: rgba(45,26,20,0.5);
  }
  .legal-body {
    display: flex;
    flex-direction: column;
    gap: 40px;
  }
  .legal-block h2 {
    font-family: var(--font-label);
    font-weight: 600;
    font-size: 18px;
    letter-spacing: 0.04em;
    color: var(--dark);
    margin-bottom: 12px;
  }
  .legal-block p {
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 1.75;
    color: rgba(45,26,20,0.75);
    margin-bottom: 10px;
  }
  .legal-block a {
    color: var(--red);
    text-decoration: underline;
    text-underline-offset: 3px;
  }
  .legal-block a:hover { opacity: 0.8; }
  .legal-back {
    margin-top: 64px;
    padding-top: 32px;
    border-top: 1px solid rgba(45,26,20,0.12);
  }
  .legal-back a {
    font-family: var(--font-body);
    font-size: 15px;
    color: var(--dark);
    opacity: 0.6;
    transition: opacity 0.2s;
  }
  .legal-back a:hover { opacity: 1; }
</style>
