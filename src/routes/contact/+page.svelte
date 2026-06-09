<script>
  import SEO from '$lib/components/SEO.svelte';

  const contactSchema = [
    {
      "@context": "https://schema.org",
      "@type": "ContactPage",
      "@id": "https://seasideparadise.ky/contact#webpage",
      "name": "Contact Seaside Paradise Restaurant",
      "description": "Get in touch with Seaside Paradise Restaurant in Bodden Town, Grand Cayman. Call, WhatsApp, email, or fill out our contact form for reservations, catering enquiries, and general questions.",
      "url": "https://seasideparadise.ky/contact",
      "isPartOf": { "@id": "https://seasideparadise.ky/#website" }
    },
    {
      "@context": "https://schema.org",
      "@type": "FAQPage",
      "mainEntity": [
        { "@type": "Question", "name": "Do I need to make a reservation?", "acceptedAnswer": { "@type": "Answer", "text": "No reservations needed. We're open every day from 11am to 9:30pm. Just walk in, find a spot on the beach terrace and we'll take care of the rest." } },
        { "@type": "Question", "name": "Do you offer catering or private events?", "acceptedAnswer": { "@type": "Answer", "text": "Yes! We cater events across Grand Cayman and host private dining events at the restaurant. Call or WhatsApp us at +1 (345) 516-4367 to discuss your event details." } },
        { "@type": "Question", "name": "What are your opening hours?", "acceptedAnswer": { "@type": "Answer", "text": "We're open Monday through Sunday, 11:00 AM to 9:30 PM — every day of the year." } },
        { "@type": "Question", "name": "What is the dress code?", "acceptedAnswer": { "@type": "Answer", "text": "Come as you are — shorts, flip flops, whatever you're wearing. We're a laid-back island spot and everyone is welcome at our table." } }
      ]
    },
    {
      "@context": "https://schema.org",
      "@type": "BreadcrumbList",
      "itemListElement": [
        { "@type": "ListItem", "position": 1, "name": "Home",    "item": "https://seasideparadise.ky/" },
        { "@type": "ListItem", "position": 2, "name": "Contact", "item": "https://seasideparadise.ky/contact" }
      ]
    }
  ];

  let form = { name: '', phone: '', email: '', message: '', agreed: false };
  let submitted = false;
  let submitting = false;
  let formError = null;

  async function handleSubmit() {
    if (!form.agreed) return;
    submitting = true;
    formError = null;
    try {
      const res = await fetch('https://formspree.io/seasideparadiseky@gmail.com', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json', 'Accept': 'application/json' },
        body: JSON.stringify({
          name: form.name,
          phone: form.phone,
          email: form.email,
          message: form.message,
        }),
      });
      if (res.ok) {
        submitted = true;
      } else {
        const data = await res.json();
        formError = data.errors?.[0]?.message || 'Something went wrong. Please try again.';
      }
    } catch {
      formError = 'Network error. Please check your connection and try again.';
    }
    submitting = false;
  }

  const faqs = [
    { q: 'Do I need to make a reservation?', a: 'No reservations needed. We\'re open every day from 11am to 9:30pm. Just walk in, find a spot on the beach terrace and we\'ll take care of the rest. Come as you are — shoes optional.' },
    { q: 'Do you offer catering or private events?', a: 'Yes! We cater events across Grand Cayman and host private dining events at the restaurant. Call or WhatsApp us at +1 (345) 516-4367 to discuss your event details.' },
    { q: 'What are your opening hours?', a: 'We\'re open Monday through Sunday, 11:00 AM to 9:30 PM — every day of the year.' },
    { q: 'What is the dress code?', a: 'Come as you are — shorts, flip flops, whatever you\'re wearing. We\'re a laid-back island spot and everyone is welcome at our table.' },
  ];
  let openFaq = 0;
  function toggleFaq(i) { openFaq = openFaq === i ? null : i; }
</script>

<SEO
  title="Contact Us — Seaside Paradise Restaurant Bodden Town, Grand Cayman"
  description="Contact Seaside Paradise Restaurant in Bodden Town, Grand Cayman. Call +1 (345) 516-4367, email seasideparadiseky@gmail.com, or fill out our contact form. Open every day 11am–9:30pm. No reservation needed."
  canonical="/contact"
  image="https://seasideparadise.ky/photos/contact-cta.jpg"
  jsonLd={contactSchema}
/>

<!-- ── HEADING + CONTACT FORM ──────────────────────────────────── -->
<section class="form-section" id="form">
  <div class="form-row-top">
    <h1 class="form-title">
      <span class="t-80">Connect</span>
      <span class="t-with"><span class="t-80">with</span> <span class="t-68">Seaside&nbsp;Paradise</span></span>
    </h1>

    <div class="contact-form-wrap">
      {#if submitted}
        <div class="success-msg">
          <span class="success-icon">✓</span>
          <h3>Message sent!</h3>
          <p>We'll get back to you shortly. See you soon at Seaside Paradise!</p>
        </div>
      {:else}
        <form on:submit|preventDefault={handleSubmit}>
          <div class="fields">
            <div class="frow">
              <input class="finput" type="text" placeholder="Full Name" bind:value={form.name} required />
              <input class="finput" type="tel" placeholder="Phone Number" bind:value={form.phone} />
            </div>
            <input class="finput" type="email" placeholder="Email Address" bind:value={form.email} required />
            <textarea class="finput ftext" placeholder="Your Message" bind:value={form.message} required></textarea>
          </div>
          <div class="checklist-btn">
            <label class="checklist">
              <input type="checkbox" bind:checked={form.agreed} required />
              <span class="cl-box" aria-hidden="true"></span>
              <span class="cl-text">I accept the <a href="/terms">Terms &amp; Condition</a></span>
            </label>
            <button type="submit" class="send-btn" disabled={submitting}>
              {submitting ? 'Sending…' : 'Send Message'}
            </button>
          </div>
          {#if formError}
            <p class="form-error">{formError}</p>
          {/if}
        </form>
      {/if}
    </div>
  </div>
</section>

<!-- ── INFORMATION ─────────────────────────────────────────────── -->
<section class="info-section">
  <div class="info-content">
    <div class="info-title">
      <span class="info-eyebrow">INFORMATION</span>
      <h2 class="info-heading">Operation Time</h2>
    </div>
    <div class="info-cols">
      <div class="info-col">
        <h3 class="info-label">Address</h3>
        <p class="info-text">166 Bodden Town Road,<br />Bodden Town, Grand Cayman, KY2-2500</p>
      </div>
      <div class="info-line"></div>
      <div class="info-col">
        <h3 class="info-label">Hours</h3>
        <p class="info-text">Mon – Sun: 11:00 AM – 9:30 PM<br />Open every day</p>
      </div>
    </div>
  </div>

  <div class="map-wrap">
    <iframe
      class="map-frame"
      src="https://maps.google.com/maps?q=Seaside+Paradise+Restaurant+166+Bodden+Town+Road+Grand+Cayman&output=embed&z=16"
      loading="lazy"
      allowfullscreen
      referrerpolicy="no-referrer-when-downgrade"
      title="Seaside Paradise Restaurant on Google Maps"
    ></iframe>
    <a href="https://maps.google.com/?q=Seaside+Paradise+Restaurant+166+Bodden+Town+Road+Grand+Cayman" target="_blank" rel="noopener" class="map-btn">View in Maps</a>
  </div>
</section>

<!-- ── CONTACT + PHOTO (Find us here) ──────────────────────────── -->
<section class="findus-section">
  <div class="findus-inner">
  <div class="findus-photo" style="background-image:url('/photos/contact-photo.jpg')"></div>
  <div class="findus-content">
    <div class="findus-title">
      <span class="findus-eyebrow">CONTACT</span>
      <h2 class="findus-heading">Find us here.</h2>
    </div>
    <div class="findus-items">
      <div class="fi-row">
        <span class="fi-label">Phone</span>
        <a class="fi-value" href="tel:+13455164367">+1 (345) 516-4367</a>
      </div>
      <div class="fi-row">
        <span class="fi-label">WhatsApp</span>
        <a class="fi-value whatsapp-link" href="https://wa.me/13455164367" target="_blank" rel="noopener">Message us on WhatsApp</a>
      </div>
      <div class="fi-row">
        <span class="fi-label">Instagram &amp; TikTok</span>
        <span class="fi-value fi-stack">
          <a href="https://instagram.com/seasideparadiserestaurant" target="_blank" rel="noopener">@seasideparadiserestaurant</a>
          <a href="https://tiktok.com/@seasideparadisefood" target="_blank" rel="noopener">@seasideparadisefood (TikTok)</a>
        </span>
      </div>
      <div class="fi-row">
        <span class="fi-label">Email</span>
        <a class="fi-value" href="mailto:seasideparadiseky@gmail.com">seasideparadiseky@gmail.com</a>
      </div>
    </div>
  </div>
  </div>
</section>

<!-- ── FAQ ─────────────────────────────────────────────────────── -->
<section class="faq-section">
  <div class="faq-inner">
  <div class="faq-left">
    {#each faqs as faq, i}
      <div class="faq-item" class:open={openFaq === i}>
        <button class="faq-q" on:click={() => toggleFaq(i)} aria-expanded={openFaq === i}>
          <span class="faq-qtext">
            {faq.q}
            {#if openFaq === i}
              <span class="faq-a">{faq.a}</span>
            {/if}
          </span>
          <svg class="faq-arrow" class:open={openFaq === i} width="32" height="24" viewBox="0 0 32 24" fill="none">
            <path d="M2 12h28M20 4l10 8-10 8" stroke="#2D1A14" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </button>
      </div>
    {/each}
  </div>
  <div class="faq-right">
    <div class="faq-title">
      <span class="faq-eyebrow">FAQ</span>
      <h2 class="faq-heading">Answers for<br />Questions</h2>
    </div>
    <a href="/contact#form" class="faq-ask">Ask A Question</a>
  </div>
  </div>
</section>

<!-- ── CTA ─────────────────────────────────────────────────────── -->
<section class="cta-section" style="background-image:url('/photos/contact-cta.jpg')">
  <div class="cta-overlay"></div>
  <h2 class="cta-title">Delve into the rich paradise<br />of flavors with our special menu.</h2>
  <div class="cta-buttons">
    <a href="/menu" class="visit-btn">Come Visit Us</a>
  </div>
</section>

<style>
  /* ── HEADING + FORM ──────────────────────────────────────────── */
  .form-section {
    background: #fffff4;
    padding: 80px 80px 100px;
  }
  .form-row-top {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 60px;
    max-width: 1280px;
    margin: 0 auto;
  }
  .form-title {
    font-family: var(--font-display);
    color: var(--dark);
    line-height: 88px;
    display: flex;
    flex-direction: column;
    flex-shrink: 0;
  }
  .t-with { display: flex; align-items: baseline; gap: 20px; }
  .t-80 { font-size: 80px; }
  .t-68 { font-size: 68px; }

  .contact-form-wrap { width: 630px; flex-shrink: 0; }
  .fields { display: flex; flex-direction: column; gap: 40px; }
  .frow { display: flex; gap: 20px; }
  .finput {
    flex: 1 0 0;
    min-width: 0;
    background: #f7f0dc;
    border: none;
    border-bottom: 1px solid var(--dark);
    padding: 0 0 20px;
    font-family: var(--font-body);
    font-size: 20px;
    line-height: 30px;
    color: var(--dark);
    outline: none;
  }
  .finput::placeholder { color: var(--dark); opacity: 0.3; }
  .ftext { width: 100%; height: 200px; resize: vertical; min-height: 140px; }

  .checklist-btn {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 40px;
    margin-top: 48px;
  }
  .checklist { display: flex; align-items: center; gap: 16px; cursor: pointer; position: relative; }
  .checklist input { position: absolute; opacity: 0; width: 20px; height: 20px; margin: 0; cursor: pointer; }
  .cl-box {
    width: 20px; height: 20px; flex-shrink: 0;
    border: 1px solid var(--red);
    background: transparent;
    transition: background 0.15s;
  }
  .checklist input:checked + .cl-box { background: var(--red); }
  .cl-text { font-family: var(--font-body); font-size: 16px; line-height: 24px; color: var(--dark); }
  .cl-text a { color: var(--red); border-bottom: 1px solid var(--red); }

  .send-btn {
    background: var(--red);
    color: var(--cream);
    border-radius: 100px;
    padding: 12px 56px;
    font-family: var(--font-label);
    font-weight: 600;
    font-size: 26px;
    line-height: 32px;
    white-space: nowrap;
    transition: opacity 0.2s;
  }
  .send-btn:hover { opacity: 0.9; }
  .send-btn:disabled { opacity: 0.6; cursor: not-allowed; }

  .form-error {
    margin-top: 12px;
    font-size: 14px;
    color: var(--red);
    font-family: var(--font-body);
  }

  .success-msg {
    text-align: center; padding: 40px;
    display: flex; flex-direction: column; align-items: center; gap: 16px;
  }
  .success-icon { font-size: 48px; color: var(--amber); }
  .success-msg h3 { font-family: var(--font-display); font-size: 28px; }
  .success-msg p { color: var(--text-muted); }

  /* ── INFORMATION ─────────────────────────────────────────────── */
  .info-section {
    background: #1a0905;
    padding: 80px 80px 88px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 64px;
  }
  .info-content { display: flex; flex-direction: column; align-items: center; gap: 48px; }
  .info-title { display: flex; flex-direction: column; align-items: center; gap: 12px; }
  .info-eyebrow { font-family: var(--font-body); font-size: 16px; line-height: 24px; letter-spacing: 1.92px; color: var(--amber); }
  .info-heading { font-family: var(--font-display); font-size: 64px; line-height: 72px; color: var(--cream); text-align: center; }
  .info-cols { display: flex; align-items: center; justify-content: center; gap: 120px; width: 900px; max-width: 100%; }
  .info-col { display: flex; flex-direction: column; align-items: center; gap: 12px; }
  .info-label { font-family: var(--font-label); font-weight: 600; font-size: 26px; line-height: 32px; color: var(--amber); }
  .info-text { font-family: var(--font-body); font-size: 16px; line-height: 24px; color: var(--cream); text-align: center; width: 252px; }
  .info-line { width: 1px; height: 160px; background: var(--amber); flex-shrink: 0; }

  .map-wrap {
    position: relative;
    width: 1280px;
    max-width: 100%;
    height: 560px;
  }
  .map-frame {
    width: 100%;
    height: 100%;
    border: 0;
    display: block;
  }
  .map-btn {
    position: absolute;
    bottom: 24px;
    right: 24px;
    background: var(--dark);
    color: var(--cream);
    border-radius: 100px;
    padding: 12px 48px;
    font-family: var(--font-body);
    font-weight: 600;
    font-size: 16px;
    line-height: 24px;
    transition: opacity 0.2s;
    z-index: 1;
  }
  .map-btn:hover { opacity: 0.9; }

  /* ── FIND US ─────────────────────────────────────────────────── */
  .findus-section {
    background: #fffff4;
    padding: clamp(48px, 5.6vw, 80px) clamp(24px, 5.6vw, 80px);
  }
  .findus-inner {
    max-width: 1280px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 80px;
  }
  .findus-photo {
    width: 630px;
    height: 522px;
    flex-shrink: 0;
    background-size: cover;
    background-position: center;
  }
  .findus-content { display: flex; flex-direction: column; gap: 56px; flex-shrink: 0; }
  .findus-title { display: flex; flex-direction: column; gap: 16px; }
  .findus-eyebrow { font-family: var(--font-body); font-size: 16px; line-height: 24px; letter-spacing: 1.92px; color: var(--red); }
  .findus-heading { font-family: var(--font-display); font-size: 64px; line-height: 72px; color: var(--dark); }
  .findus-items { display: flex; flex-direction: column; gap: 20px; }
  .fi-row {
    display: flex; align-items: flex-start; justify-content: space-between; gap: 24px;
    width: 542px; max-width: 100%;
    padding-bottom: 20px;
    border-bottom: 1px solid rgba(45,26,20,0.2);
  }
  .fi-label { font-family: var(--font-body); font-weight: 600; font-size: 20px; line-height: 30px; color: var(--dark); }
  .fi-value { font-family: var(--font-body); font-size: 20px; line-height: 30px; color: var(--dark); opacity: 0.5; text-align: right; }
  .fi-stack { display: flex; flex-direction: column; }
  .fi-value a:hover { opacity: 1; color: var(--red); }
  .whatsapp-link { color: #25D366; opacity: 0.85; }
  .whatsapp-link:hover { opacity: 1; color: #25D366 !important; }

  /* ── FAQ ─────────────────────────────────────────────────────── */
  .faq-section {
    background: #fffff4;
    padding: 0 clamp(24px, 5.6vw, 80px) clamp(60px, 8vw, 120px);
  }
  .faq-inner {
    max-width: 1280px;
    margin: 0 auto;
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    gap: 80px;
  }
  .faq-left { display: flex; flex-direction: column; gap: 16px; width: 700px; flex-shrink: 0; }
  .faq-item { border: 1px solid rgba(45,26,20,0.2); transition: border-color 0.2s; }
  .faq-item.open { border-color: var(--dark); }
  .faq-q {
    width: 100%;
    display: flex; align-items: flex-start; justify-content: space-between; gap: 24px;
    padding: 24px;
    text-align: left;
  }
  .faq-qtext {
    display: flex; flex-direction: column; gap: 8px;
    font-family: var(--font-display); font-size: 36px; line-height: 42px; color: var(--dark);
  }
  .faq-a {
    font-family: var(--font-body); font-size: 20px; line-height: 30px;
    color: var(--dark); opacity: 0.7; font-weight: 400;
  }
  .faq-arrow { flex-shrink: 0; margin-top: 12px; transition: transform 0.3s; }
  .faq-arrow.open { transform: rotate(90deg); }

  .faq-right {
    display: flex; flex-direction: column; align-items: flex-end;
    justify-content: space-between; align-self: stretch;
    text-align: right; flex-shrink: 0;
  }
  .faq-title { display: flex; flex-direction: column; align-items: flex-end; gap: 16px; }
  .faq-eyebrow { font-family: var(--font-body); font-size: 16px; line-height: 24px; letter-spacing: 1.92px; color: var(--red); }
  .faq-heading { font-family: var(--font-display); font-size: 80px; line-height: 88px; color: var(--dark); }
  .faq-ask {
    border: 1px solid var(--red);
    color: var(--red);
    border-radius: 100px;
    padding: 8px 32px;
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 24px;
    transition: background 0.2s, color 0.2s;
  }
  .faq-ask:hover { background: var(--red); color: var(--cream); }

  /* ── CTA ─────────────────────────────────────────────────────── */
  .cta-section {
    position: relative;
    min-height: 618px;
    background-size: cover;
    background-position: center;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: space-between;
    padding: 64px 80px;
  }
  .cta-overlay { position: absolute; inset: 0; background: rgba(16,5,1,0.45); }
  .cta-title {
    position: relative; z-index: 1;
    font-family: var(--font-display);
    font-size: 80px;
    line-height: 88px;
    color: var(--cream);
  }
  .cta-buttons { position: relative; z-index: 1; width: 100%; display: flex; justify-content: flex-end; }
  .visit-btn {
    background: var(--cream);
    color: var(--dark);
    border-radius: 100px;
    padding: 12px 56px;
    font-family: var(--font-label);
    font-weight: 600;
    font-size: 26px;
    line-height: 32px;
    transition: opacity 0.2s;
  }
  .visit-btn:hover { opacity: 0.9; }

  /* ── RESPONSIVE ──────────────────────────────────────────────── */
  @media (max-width: 1180px) {
    .form-row-top { flex-direction: column; align-items: flex-start; gap: 48px; }
    .contact-form-wrap { width: 100%; }
    .findus-inner { flex-direction: column; align-items: stretch; }
    .findus-photo { width: 100%; }
    .fi-row { width: 100%; }
    .faq-inner { flex-direction: column; }
    .faq-left { width: 100%; }
    .faq-right { align-self: auto; align-items: flex-start; text-align: left; gap: 32px; }
    .faq-title { align-items: flex-start; }
  }

  @media (max-width: 720px) {
    .form-section { padding: 56px 24px 64px; }
    .t-80 { font-size: 48px; }
    .t-68 { font-size: 42px; }
    .form-title { line-height: 56px; }
    .t-with { flex-wrap: wrap; gap: 12px; }
    .info-section { padding: 56px 24px; }
    .info-heading { font-size: 40px; line-height: 48px; }
    .info-cols { flex-direction: column; gap: 40px; width: 100%; }
    .info-line { width: 160px; height: 1px; }
    .map-wrap { height: 360px; }
    .findus-section { padding: 40px 24px; }
    .findus-heading { font-size: 44px; line-height: 52px; }
    .findus-photo { height: 320px; }
    .frow { flex-direction: column; gap: 40px; }
    .checklist-btn { flex-direction: column; align-items: stretch; gap: 24px; }
    .send-btn { width: 100%; font-size: 20px; padding: 12px 32px; }
    .faq-section { padding: 0 24px 64px; }
    .faq-qtext { font-size: 26px; line-height: 32px; }
    .faq-a { font-size: 16px; line-height: 24px; }
    .faq-heading { font-size: 52px; line-height: 60px; }
    .cta-section { min-height: 460px; padding: 48px 24px; }
    .cta-title { font-size: 40px; line-height: 48px; }
    .visit-btn { font-size: 20px; padding: 12px 32px; }
  }
</style>
