<script>
  let form = { name: '', phone: '', email: '', message: '', agreed: false };
  let submitted = false;
  let submitting = false;

  async function handleSubmit() {
    if (!form.agreed) return;
    submitting = true;
    await new Promise(r => setTimeout(r, 800));
    submitted = true;
    submitting = false;
  }

  const faqs = [
    { q: 'Do I need to make a reservation?', a: 'No reservations needed. We\'re open every day from 11am to 10:30pm. Just walk in, find a spot on the beach terrace and we\'ll take care of the rest. Come as you are — shoes optional.' },
    { q: 'Do you offer catering or private events?', a: 'Yes! We cater events across Grand Cayman and host private dining events at the restaurant. Call or WhatsApp us at +1 (345) 516-4367 to discuss your event details.' },
    { q: 'What is the dress code?', a: 'Come as you are — shorts, flip flops, whatever you\'re wearing. We\'re a laid-back island spot and everyone is welcome at our table.' },
    { q: 'What are the payment methods?', a: 'We accept cash and cards.' },
  ];
  let openFaq = null;
  function toggleFaq(i) { openFaq = openFaq === i ? null : i; }
</script>

<svelte:head>
  <title>Contact — Seaside Paradise Restaurant</title>
</svelte:head>

<!-- CONTACT FORM -->
<section class="contact-hero">
  <div class="contact-inner">
    <div class="contact-left">
      <h1 class="display contact-title">Connect<br />with<br />Seaside Paradise</h1>
    </div>
    <div class="contact-right">
      {#if submitted}
        <div class="success-msg">
          <span class="success-icon">✓</span>
          <h3>Message sent!</h3>
          <p>We'll get back to you shortly. See you soon at Seaside Paradise!</p>
        </div>
      {:else}
        <form on:submit|preventDefault={handleSubmit} class="contact-form">
          <div class="form-row">
            <div class="field">
              <label for="name">Full Name</label>
              <input id="name" type="text" placeholder="Full Name" bind:value={form.name} required />
            </div>
            <div class="field">
              <label for="phone">Phone Number</label>
              <input id="phone" type="tel" placeholder="Phone Number" bind:value={form.phone} />
            </div>
          </div>
          <div class="field">
            <label for="email">Email Address</label>
            <input id="email" type="email" placeholder="Email Address" bind:value={form.email} required />
          </div>
          <div class="field">
            <label for="message">Your Message</label>
            <textarea id="message" rows="5" placeholder="Your Message" bind:value={form.message} required></textarea>
          </div>
          <div class="checkbox-row">
            <input type="checkbox" id="agreed" bind:checked={form.agreed} required />
            <label for="agreed">I accept the <a href="/terms">Terms &amp; Conditions</a></label>
          </div>
          <button type="submit" class="btn btn-red submit-btn" disabled={submitting}>
            {submitting ? 'Sending...' : 'Send Message'}
          </button>
        </form>
      {/if}
    </div>
  </div>
</section>

<!-- OPERATION TIME -->
<section class="operation-section">
  <div class="container op-inner">
    <span class="label">Information</span>
    <h2 class="display op-title">Operation Time</h2>
    <div class="op-grid">
      <div class="op-item">
        <h3>Address</h3>
        <p>166 Bodden Town Road,<br />Bodden Town, Grand Cayman, KY2-2500</p>
      </div>
      <div class="op-item">
        <h3>Hours</h3>
        <p>Mon – Sun: 11:00 AM – 10:30 PM<br />Open every day</p>
      </div>
      <div class="op-item">
        <a href="https://maps.google.com/?q=Seaside+Paradise+Restaurant+Bodden+Town" target="_blank" rel="noopener" class="map-link">View in Maps →</a>
      </div>
    </div>
  </div>
</section>

<!-- FIND US -->
<section class="findus-section">
  <div class="findus-photo photo-bg" style="background-image:url('/photos/restaurant-exterior.jpg')">
    <div class="findus-overlay"></div>
  </div>
  <div class="findus-content">
    <span class="label">Contact</span>
    <h2 class="display">Find us here.</h2>

    <div class="contact-details">
      <div class="contact-item">
        <span class="item-label">Phone</span>
        <a href="tel:+13455164367">+1 (345) 516-4367</a>
      </div>
      <div class="contact-item">
        <span class="item-label">Instagram &amp; TikTok</span>
        <a href="https://instagram.com/seasideparadiserestaurant" target="_blank" rel="noopener">@seasideparadiserestaurant</a>
        <a href="https://tiktok.com/@seasideparadisefood" target="_blank" rel="noopener">@seasideparadisefood (TikTok)</a>
      </div>
      <div class="contact-item">
        <span class="item-label">Email</span>
        <a href="mailto:seasideparadiseky@gmail.com">seasideparadiseky@gmail.com</a>
      </div>
    </div>

    <a href="tel:+13455164367" class="btn btn-red call-btn">Call +1 (345) 516-4367</a>
  </div>
</section>

<!-- MAP -->
<div class="map-section">
  <iframe
    title="Seaside Paradise Restaurant Location"
    src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3789.2!2d-81.2!3d19.3!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2sSeaside+Paradise+Restaurant!5e0!3m2!1sen!2sky!4v1234567890"
    width="100%" height="320"
    style="border:0;"
    allowfullscreen
    loading="lazy"
    referrerpolicy="no-referrer-when-downgrade"
  ></iframe>
</div>

<!-- FAQ -->
<section class="faq-section">
  <div class="container faq-inner">
    <div class="faq-left">
      <span class="label">FAQ</span>
      <h2 class="display">Answers for<br />Questions</h2>
    </div>
    <div class="faq-right">
      {#each faqs as faq, i}
        <div class="faq-item">
          <button class="faq-q" on:click={() => toggleFaq(i)} aria-expanded={openFaq === i}>
            <span>{faq.q}</span>
            <svg class="faq-icon" class:open={openFaq === i} width="16" height="16" viewBox="0 0 16 16">
              <path d="M3 6l5 5 5-5" stroke="var(--red)" stroke-width="1.5" stroke-linecap="round" fill="none"/>
            </svg>
          </button>
          {#if openFaq === i}
            <p class="faq-a">{faq.a}</p>
          {/if}
          <div class="faq-divider"></div>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- CTA -->
<section class="contact-cta photo-bg" style="background-image:url('/photos/beach-trees.jpg')">
  <div class="cta-overlay"></div>
  <div class="container cta-inner">
    <h2 class="display cta-title">Come as you are.<br /><em>Eat like a local.</em></h2>
    <a href="/menu" class="btn btn-outline-cream">Get in Touch →</a>
  </div>
</section>

<style>
/* CONTACT HERO */
.contact-hero {
  background: var(--offwhite);
  padding: clamp(60px, 8vw, 120px) 0;
}
.contact-inner {
  display: grid; grid-template-columns: 1fr 1.2fr;
  gap: 80px; align-items: center;
  max-width: var(--container); margin: 0 auto;
  padding: 0 clamp(20px, 5vw, 80px);
}
.contact-title { font-size: clamp(36px, 6vw, 72px); }

/* FORM */
.contact-form { display: flex; flex-direction: column; gap: 16px; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
.field { display: flex; flex-direction: column; gap: 6px; }
.field label { font-size: 13px; font-weight: 600; color: var(--text-muted); }
.field input, .field textarea {
  background: var(--cream);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 14px 16px;
  font-family: var(--font-body); font-size: 15px; color: var(--dark);
  outline: none; transition: border-color 0.2s;
}
.field input:focus, .field textarea:focus { border-color: var(--amber); }
.field textarea { resize: vertical; min-height: 120px; }
.checkbox-row { display: flex; align-items: center; gap: 10px; font-size: 14px; color: var(--text-muted); }
.checkbox-row input { width: 16px; height: 16px; accent-color: var(--red); }
.checkbox-row a { color: var(--red); text-decoration: underline; }
.submit-btn { width: 100%; justify-content: center; padding: 16px; font-size: 15px; }
.submit-btn:disabled { opacity: 0.6; cursor: not-allowed; }

.success-msg {
  text-align: center; padding: 60px 40px;
  display: flex; flex-direction: column; align-items: center; gap: 16px;
}
.success-icon { font-size: 48px; color: var(--amber); }
.success-msg h3 { font-family: var(--font-display); font-size: 28px; }
.success-msg p { color: var(--text-muted); }

/* OPERATION TIME */
.operation-section { background: var(--bg-dark); padding: var(--section-pad) 0; }
.op-inner { display: flex; flex-direction: column; gap: 32px; }
.operation-section .label { color: var(--amber); }
.op-title { font-size: clamp(28px, 4vw, 48px); color: var(--cream); }
.op-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 40px; }
.op-item h3 { font-family: var(--font-label); font-weight: 600; font-size: 14px; letter-spacing: 0.06em; color: var(--amber); margin-bottom: 10px; }
.op-item p { font-size: 15px; color: rgba(247,240,220,0.75); line-height: 1.7; }
.map-link { color: var(--amber); font-size: 14px; font-weight: 600; }

/* FIND US */
.findus-section { display: grid; grid-template-columns: 1fr 1fr; min-height: 500px; }
.findus-photo { position: relative; background-color: #5A7060; }
.findus-overlay { position: absolute; inset: 0; background: rgba(26,9,5,0.3); }
.findus-content {
  background: var(--cream);
  padding: clamp(48px, 6vw, 80px) clamp(32px, 5vw, 64px);
  display: flex; flex-direction: column; gap: 24px;
}
.findus-content .label { display: block; }
.findus-content h2 { font-size: clamp(28px, 4vw, 44px); }
.contact-details { display: flex; flex-direction: column; gap: 20px; }
.contact-item { display: flex; flex-direction: column; gap: 4px; }
.item-label {
  font-family: var(--font-label); font-size: 11px; letter-spacing: 0.1em;
  text-transform: uppercase; color: var(--amber); font-weight: 600;
}
.contact-item a { font-size: 15px; color: var(--dark); transition: color 0.2s; }
.contact-item a:hover { color: var(--red); }
.call-btn { margin-top: 8px; }

/* MAP */
.map-section { background: #e0e8e4; }

/* FAQ */
.faq-section { background: var(--offwhite); padding: var(--section-pad) 0; }
.faq-inner { display: grid; grid-template-columns: 1fr 1.4fr; gap: 80px; align-items: start; }
.faq-left h2 { font-size: clamp(28px, 4vw, 44px); margin-top: 8px; }
.faq-q {
  width: 100%; display: flex; align-items: center; justify-content: space-between; gap: 16px;
  padding: 20px 0; font-family: var(--font-display); font-size: clamp(16px, 2vw, 20px);
  color: var(--dark); text-align: left; transition: color 0.2s;
}
.faq-q:hover { color: var(--red); }
.faq-icon { flex-shrink: 0; transition: transform 0.3s; }
.faq-icon.open { transform: rotate(180deg); }
.faq-a { padding-bottom: 20px; font-size: 15px; color: var(--text-muted); line-height: 1.7; }
.faq-divider { height: 1px; background: var(--border); }

/* CTA */
.contact-cta { position: relative; min-height: 360px; display: flex; align-items: center; background-color: #3D5A50; }
.cta-overlay { position: absolute; inset: 0; background: rgba(26,9,5,0.6); }
.cta-inner {
  position: relative; z-index: 1;
  padding: 80px clamp(20px, 5vw, 80px);
  display: flex; flex-direction: column; align-items: flex-start; gap: 28px;
}
.cta-title { font-size: clamp(28px, 5vw, 52px); color: var(--cream); line-height: 1.1; }
.cta-title em { font-style: normal; color: var(--amber); }

@media (max-width: 768px) {
  .contact-inner { grid-template-columns: 1fr; gap: 48px; }
  .form-row { grid-template-columns: 1fr; }
  .op-grid { grid-template-columns: 1fr; }
  .findus-section { grid-template-columns: 1fr; }
  .findus-photo { height: 280px; }
  .faq-inner { grid-template-columns: 1fr; gap: 40px; }
}
</style>
