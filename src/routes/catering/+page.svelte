<script>
  const photos = [
    '/photos/services-interior.jpg',
    '/photos/about-hero.jpg',
    '/photos/values-bg.jpg',
  ];
  let photoIndex = 0;
  function prevPhoto() { photoIndex = (photoIndex - 1 + photos.length) % photos.length; }
  function nextPhoto() { photoIndex = (photoIndex + 1) % photos.length; }
</script>

<svelte:head>
  <title>Services & Catering — Seaside Paradise</title>
</svelte:head>

<!-- ── HERO ── -->
<section class="services-hero photo-bg" style="background-image:url('/photos/services-hero.jpg')">
  <div class="hero-overlay"></div>
  <div class="hero-title-wrap">
    <h1 class="hero-title">
      <span>What We</span>
      <span class="hero-title-row"><span>Do</span><span>For You</span></span>
    </h1>
  </div>
</section>

<!-- ── OUR OFFERING ── -->
<section class="offering-section">
  <div class="offering-header">
    <p class="eyebrow-red">OUR OFFERING</p>
    <h2 class="offering-title">Fresh, Local &amp; Catered to You</h2>
  </div>

  <div class="offering-photo-wrap">
    <div class="offering-photo photo-bg" style="background-image:url('{photos[photoIndex]}')">
      <button class="photo-arrow arrow-left" aria-label="Previous photo" on:click={prevPhoto}>
        <svg width="32" height="32" viewBox="0 0 32 32" fill="none"><path d="M20 26L10 16L20 6" stroke="#2D1A14" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
      </button>
      <button class="photo-arrow arrow-right" aria-label="Next photo" on:click={nextPhoto}>
        <svg width="32" height="32" viewBox="0 0 32 32" fill="none"><path d="M12 6L22 16L12 26" stroke="#2D1A14" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
      </button>
    </div>
    <div class="photo-dots">
      {#each photos as _, i}
        <button class="photo-dot" class:active={photoIndex === i} on:click={() => photoIndex = i} aria-label="Photo {i + 1}"></button>
      {/each}
    </div>
  </div>

  <div class="offering-footer">
    <p class="offering-body">Whether you're sitting down for lunch or planning a big gathering, Seaside Paradise has you covered. From daily dining to full catering, we bring the island flavors to you.</p>
    <a href="/contact" class="btn-pill-red">Get in Touch</a>
  </div>
</section>

<!-- ── PRIVATE EVENTS ── -->
<section class="events-section">
  <div class="events-photo photo-bg" style="background-image:url('/photos/services-private.jpg')"></div>
  <div class="events-content">
    <div class="events-text">
      <div class="events-head">
        <p class="eyebrow-amber">BOOK US</p>
        <h2 class="events-title">Private Events<br />&amp; Catering</h2>
      </div>
      <p class="events-body">Celebrate your next birthday, graduation, anniversary or corporate gathering with us. We cook fresh Caribbean dishes for your group and make the occasion one to remember.</p>
    </div>
    <a href="/contact" class="btn-pill-cream">Book Your Event</a>
  </div>
</section>

<!-- ── SERVICE ITEMS ── -->
<section class="items-section">
  <div class="items-inner">
    <div class="service-item">
      <div class="service-photo photo-bg" style="background-image:url('/photos/services-offsite.jpg')">
        <div class="service-label">Off-Site Catering</div>
      </div>
      <p class="service-desc">We bring Seaside Paradise to your event — fresh Caribbean dishes, hot and ready for your guests anywhere in Grand Cayman. Call us to discuss your menu and headcount.</p>
    </div>
    <div class="service-item">
      <div class="service-photo photo-bg" style="background-image:url('/photos/services-drinks.jpg')">
        <div class="service-label">Island Drinks &amp; Sides</div>
      </div>
      <p class="service-desc">Pair your meal with our locally-inspired rum punch, bush rum cocktails, and fresh-squeezed island juices.</p>
    </div>
  </div>
</section>

<style>
/* ── Shared eyebrows ── */
.eyebrow-red {
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 24px;
  letter-spacing: 1.92px;
  color: var(--red);
}
.eyebrow-amber {
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 24px;
  letter-spacing: 1.92px;
  color: var(--amber);
}

/* ── Shared buttons ── */
.btn-pill-red {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: var(--red);
  color: var(--cream);
  font-family: var(--font-label);
  font-weight: 600;
  font-size: 26px;
  line-height: 32px;
  padding: 12px 56px;
  border-radius: 100px;
  white-space: nowrap;
  transition: opacity 0.2s;
  text-decoration: none;
  flex-shrink: 0;
}
.btn-pill-red:hover { opacity: 0.9; }

.btn-pill-cream {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: var(--cream);
  color: var(--dark);
  font-family: var(--font-label);
  font-weight: 600;
  font-size: 26px;
  line-height: 32px;
  padding: 12px 56px;
  border-radius: 100px;
  white-space: nowrap;
  transition: opacity 0.2s;
  text-decoration: none;
  flex-shrink: 0;
}
.btn-pill-cream:hover { opacity: 0.9; }

/* ── HERO ── */
.services-hero {
  position: relative;
  height: 400px;
  margin-top: calc(-1 * var(--navbar-h));
  background-color: #4A6060;
  background-size: cover;
  background-position: center;
}
.hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(26,9,5,0.72) 0%, rgba(26,9,5,0.3) 55%, rgba(26,9,5,0.1) 100%);
}
.hero-title-wrap {
  position: absolute;
  bottom: 0;
  left: 0;
  padding: 0 0 0 clamp(24px, 5.6vw, 80px);
  z-index: 1;
}
.hero-title {
  font-family: var(--font-display);
  font-size: clamp(48px, 6vw, 80px);
  line-height: 1.1;
  color: var(--cream);
  display: flex;
  flex-direction: column;
}
.hero-title-row {
  display: flex;
  gap: 0.25em;
  align-items: baseline;
}

/* ── OFFERING ── */
.offering-section {
  background: #fffff4;
  display: flex;
  flex-direction: column;
  gap: 56px;
  padding: var(--section-pad) clamp(24px, 5.6vw, 80px);
}
.offering-header {
  display: flex;
  flex-direction: column;
  gap: 16px;
  align-items: center;
  text-align: center;
  max-width: var(--container);
  margin: 0 auto;
  width: 100%;
}
.offering-title {
  font-family: var(--font-display);
  font-size: clamp(32px, 5vw, 64px);
  line-height: 1.12;
  color: var(--dark);
  text-align: center;
}
.offering-photo-wrap {
}
.photo-dots {
  display: flex;
  gap: 8px;
  justify-content: center;
  padding: 16px 0 0;
}
.photo-dot {
  width: 8px;
  height: 8px;
  border-radius: 100px;
  background: rgba(45,26,20,0.2);
  border: none;
  cursor: pointer;
  padding: 0;
  transition: width 0.25s ease, background 0.25s ease;
}
.photo-dot.active { width: 28px; background: var(--dark); }
.offering-photo {
  position: relative;
  width: 100%;
  max-width: 1280px;
  margin: 0 auto;
  height: clamp(280px, 40vw, 520px);
  background-color: #4A7060;
  background-size: cover;
  background-position: center;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 40px;
}
.photo-arrow {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  background: var(--cream);
  display: flex;
  align-items: center;
  justify-content: center;
  border: none;
  cursor: pointer;
  opacity: 0.85;
  transition: opacity 0.2s;
  flex-shrink: 0;
}
.photo-arrow:hover { opacity: 1; }

.offering-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 40px;
  flex-wrap: wrap;
  max-width: var(--container);
  margin: 0 auto;
  width: 100%;
}
.offering-body {
  font-family: var(--font-body);
  font-size: clamp(16px, 1.5vw, 20px);
  line-height: 30px;
  color: var(--dark);
  opacity: 0.7;
  max-width: 660px;
}

/* ── PRIVATE EVENTS ── */
.events-section {
  display: flex;
  align-items: stretch;
  min-height: 800px;
}
.events-photo {
  flex: 1;
  min-width: 0;
  background-color: #4A6858;
  background-size: cover;
  background-position: center;
  min-height: 480px;
}
.events-content {
  flex: 1;
  min-width: 0;
  background: var(--bg-dark);
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 72px;
  padding: clamp(48px, 5.6vw, 80px);
}
.events-text {
  display: flex;
  flex-direction: column;
  gap: 30px;
}
.events-head {
  display: flex;
  flex-direction: column;
  gap: 16px;
}
.events-title {
  font-family: var(--font-display);
  font-size: clamp(40px, 6vw, 80px);
  line-height: 1.1;
  color: var(--cream);
}
.events-body {
  font-family: var(--font-body);
  font-size: clamp(16px, 1.5vw, 20px);
  line-height: 30px;
  color: var(--cream);
  opacity: 0.7;
  max-width: 550px;
}

/* ── SERVICE ITEMS ── */
.items-section {
  background: #fffff4;
  padding: var(--section-pad) clamp(24px, 5.6vw, 80px);
}
.items-inner {
  max-width: 1280px;
  margin: 0 auto;
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 40px;
  flex-wrap: wrap;
}
.service-item {
  display: flex;
  flex-direction: column;
  gap: 24px;
  flex: 1;
  min-width: min(100%, 480px);
}
.service-photo {
  position: relative;
  width: 100%;
  aspect-ratio: 620 / 480;
  background-color: #4A7060;
  background-size: cover;
  background-position: center;
  display: flex;
  align-items: flex-end;
  justify-content: center;
  overflow: hidden;
}
.service-label {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  background: var(--cream);
  padding: 20px;
  font-family: var(--font-label);
  font-weight: 600;
  font-size: 26px;
  line-height: 32px;
  color: var(--dark);
  white-space: nowrap;
}
.service-desc {
  font-family: var(--font-body);
  font-size: clamp(16px, 1.5vw, 20px);
  line-height: 30px;
  color: var(--dark);
  opacity: 0.7;
  text-align: center;
}

/* ── RESPONSIVE ── */
@media (max-width: 900px) {
  .services-hero {
    margin-top: calc(-1 * var(--navbar-h-mobile));
    min-height: calc(100svh + var(--navbar-h-mobile));
  }
  .events-section { flex-direction: column; }
  .events-photo { min-height: 360px; }
  .offering-footer { flex-direction: column; align-items: flex-start; }
}
@media (max-width: 600px) {
  .services-hero { height: 320px; }
  .photo-arrow { width: 48px; height: 48px; }
  .service-label { bottom: 16px; font-size: 20px; padding: 14px; }
  .items-inner { gap: 56px; }
}
</style>
