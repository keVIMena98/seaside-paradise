<script>
  import SEO from '$lib/components/SEO.svelte';
</script>

<SEO
  title="Terms & Conditions | Seaside Paradise Restaurant"
  description="Terms and Conditions for Seaside Paradise Restaurant, Bodden Town, Grand Cayman. Read our policies for dining, catering, and website use."
  canonical="/terms"
/>

<section class="legal-section">
  <div class="legal-inner">
    <div class="legal-header">
      <p class="eyebrow">LEGAL</p>
      <h1 class="legal-title">Terms &amp; Conditions</h1>
      <p class="legal-date">Last updated: June 2026</p>
    </div>

    <div class="legal-body">
      <div class="legal-block">
        <h2>1. Use of This Website</h2>
        <p>By accessing and using the Seaside Paradise Restaurant website, you agree to these terms and conditions. This website is operated by Rodneys Group Ltd and is intended for informational purposes and to facilitate contact with the restaurant.</p>
      </div>

      <div class="legal-block">
        <h2>2. Contact Form</h2>
        <p>When you submit our contact form, you are providing personal information for the purpose of receiving a response from us. Please only submit accurate information. We will not use your contact details for unsolicited marketing.</p>
      </div>

      <div class="legal-block">
        <h2>3. Menu &amp; Pricing</h2>
        <p>Menu items and prices displayed on this website are for informational purposes only and are subject to change without notice. The daily rotating menu is determined each morning based on ingredient availability. Please contact us directly to confirm today's offerings.</p>
      </div>

      <div class="legal-block">
        <h2>4. Catering &amp; Private Events</h2>
        <p>Enquiries submitted through this website do not constitute a confirmed booking. All catering and private event arrangements must be confirmed directly with the restaurant by phone or email. A deposit may be required to secure your booking.</p>
      </div>

      <div class="legal-block">
        <h2>5. Intellectual Property</h2>
        <p>All content on this website, including text, photographs, and the Seaside Paradise logo, is the property of Rodneys Group Ltd. You may not reproduce, distribute, or use any content from this website without prior written permission.</p>
      </div>

      <div class="legal-block">
        <h2>6. Limitation of Liability</h2>
        <p>Rodneys Group Ltd makes no warranties, express or implied, regarding the accuracy or completeness of information on this website. We are not liable for any loss or damage arising from your use of this website or reliance on any information provided herein.</p>
      </div>

      <div class="legal-block">
        <h2>7. Changes to These Terms</h2>
        <p>We reserve the right to update these terms at any time. Continued use of the website after any changes constitutes your acceptance of the new terms.</p>
      </div>

      <div class="legal-block">
        <h2>8. Governing Law</h2>
        <p>These terms are governed by the laws of the Cayman Islands. Any disputes shall be subject to the exclusive jurisdiction of the courts of the Cayman Islands.</p>
      </div>

      <div class="legal-block">
        <h2>9. Contact</h2>
        <p>For any questions regarding these terms, please contact us at:</p>
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
