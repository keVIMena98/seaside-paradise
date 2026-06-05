<svelte:head>
  <title>Services & Catering — Seaside Paradise Restaurant</title>
</svelte:head>

<!-- HERO -->
<section class="services-hero photo-bg" style="background-image:url('/photos/services-hero.jpg')">
  <div class="hero-overlay"></div>
  <div class="container hero-content">
    <span class="label">What We Do</span>
    <h1 class="display hero-title">What We<br />Do<br />For You</h1>
  </div>
</section>

<!-- INTRO -->
<section class="intro-section">
  <div class="container intro-inner">
    <div class="intro-text">
      <span class="label">Our Offering</span>
      <h2 class="display">Fresh, Local &amp; Catered to You</h2>
      <p>Whether you're sitting down for lunch or planning a big gathering, Seaside Paradise has you covered. From daily dining to full catering, we bring the island flavors to you.</p>
      <a href="/contact" class="btn btn-dark">Get in Touch</a>
    </div>
    <div class="intro-photo photo-bg" style="background-image:url('/photos/fine-dining.jpg')">
      <div class="photo-caption">Seaside Paradise, Bodden Town</div>
    </div>
  </div>
</section>

<!-- DAILY DINING -->
<section class="daily-section">
  <div class="daily-photo photo-bg" style="background-image:url('/photos/daily-dining.jpg')"></div>
  <div class="daily-content">
    <span class="label">Fresh Off the Grill, Every Day</span>
    <h2 class="display">Daily Dining</h2>
    <p>Open 7 days a week, 11am–10:30pm. Fresh Caribbean dishes cooked daily. Walk in and eat well.</p>
    <a href="/menu" class="btn btn-dark">See Our Menu</a>
  </div>
</section>

<!-- PRIVATE EVENTS -->
<section class="events-section">
  <div class="events-photo photo-bg" style="background-image:url('/photos/private-events.jpg')"></div>
  <div class="events-content">
    <span class="label">Book Us</span>
    <h2 class="display events-title">Private Events<br />&amp; Catering</h2>
    <p>Celebrate your next birthday, graduation, anniversary or corporate gathering with us. We cook fresh Caribbean dishes for your group and make the occasion one to remember.</p>
    <a href="/contact" class="btn btn-outline-cream">Book Your Event</a>
  </div>
</section>

<!-- OFF-SITE CATERING -->
<section class="offsite-section">
  <div class="container offsite-inner">
    <div class="service-card">
      <div class="service-icon">🍽️</div>
      <h3>Off-Site Catering</h3>
      <p>We bring Seaside Paradise to your event — fresh Caribbean dishes, hot and ready for your guests anywhere in Grand Cayman. Call us to discuss your menu and headcount.</p>
      <a href="/contact" class="btn btn-outline-dark">Get a Quote</a>
    </div>
    <div class="service-card">
      <div class="service-icon">🍹</div>
      <h3>Island Drinks &amp; Sides</h3>
      <p>Pair your meal with our locally-inspired rum punch, bush rum cocktails, and fresh-squeezed island juices. The perfect complement to any Caribbean spread.</p>
      <a href="/contact" class="btn btn-outline-dark">Ask About Drinks</a>
    </div>
  </div>
</section>

<!-- CTA -->
<section class="services-cta photo-bg" style="background-image:url('/photos/beach-trees.jpg')">
  <div class="cta-overlay"></div>
  <div class="container cta-content">
    <h2 class="display cta-text">Good food,<br /><em>good vibes,</em><br />every day.</h2>
    <a href="/contact" class="btn btn-outline-cream">Get in Touch</a>
  </div>
</section>

<style>
/* HERO */
.services-hero {
  position: relative;
  height: 560px;
  display: flex;
  align-items: flex-end;
  background-color: #4A6060;
}
.hero-overlay { position: absolute; inset: 0; background: rgba(26,9,5,0.55); }
.hero-content {
  position: relative; z-index: 1;
  padding-bottom: 64px;
}
.hero-content .label { display: block; color: var(--amber); margin-bottom: 8px; }
.hero-title { font-size: clamp(40px, 7vw, 80px); color: var(--cream); line-height: 1.0; }

/* INTRO */
.intro-section { background: var(--cream); padding: var(--section-pad) 0; }
.intro-inner {
  display: grid; grid-template-columns: 1fr 1fr;
  gap: 80px; align-items: center;
}
.intro-text { display: flex; flex-direction: column; gap: 20px; }
.intro-text .label { display: block; }
.intro-text h2 { font-size: clamp(28px, 4vw, 44px); }
.intro-text p { font-size: 16px; color: var(--text-muted); line-height: 1.7; }
.intro-photo {
  position: relative;
  height: 400px;
  border-radius: var(--radius);
  overflow: hidden;
  background-color: #5A7060;
}
.photo-caption {
  position: absolute; bottom: 0; left: 0; right: 0;
  background: rgba(26,9,5,0.6);
  color: rgba(247,240,220,0.8);
  font-size: 12px;
  padding: 10px 16px;
}

/* DAILY DINING */
.daily-section {
  display: grid; grid-template-columns: 1fr 1fr;
  min-height: 500px;
}
.daily-photo { background-color: #4A7060; }
.daily-content {
  background: var(--offwhite);
  padding: clamp(48px, 6vw, 96px) clamp(40px, 5vw, 80px);
  display: flex; flex-direction: column;
  justify-content: center; gap: 20px;
}
.daily-content .label { display: block; }
.daily-content h2 { font-size: clamp(32px, 4vw, 52px); }
.daily-content p { font-size: 16px; color: var(--text-muted); line-height: 1.7; max-width: 380px; }

/* PRIVATE EVENTS */
.events-section {
  display: grid; grid-template-columns: 1fr 1fr;
  min-height: 560px;
}
.events-photo {
  order: 2;
  background-color: #4A6858;
  background-size: cover;
  background-position: center;
}
.events-content {
  order: 1;
  background: var(--bg-dark);
  padding: clamp(48px, 6vw, 96px) clamp(40px, 5vw, 80px);
  display: flex; flex-direction: column;
  justify-content: center; gap: 20px;
}
.events-content .label { color: var(--amber); display: block; }
.events-title { font-size: clamp(32px, 4vw, 52px); color: var(--cream); }
.events-content p { font-size: 16px; color: rgba(247,240,220,0.7); line-height: 1.7; max-width: 380px; }

/* OFF-SITE */
.offsite-section { background: var(--cream); padding: var(--section-pad) 0; }
.offsite-inner { display: grid; grid-template-columns: repeat(2, 1fr); gap: 32px; }
.service-card {
  background: var(--offwhite);
  padding: 40px 36px;
  border-top: 4px solid var(--amber);
  display: flex; flex-direction: column; gap: 16px;
  border-radius: var(--radius);
}
.service-icon { font-size: 32px; }
.service-card h3 { font-family: var(--font-label); font-weight: 600; font-size: 22px; }
.service-card p { font-size: 15px; color: var(--text-muted); line-height: 1.7; flex: 1; }

/* CTA */
.services-cta {
  position: relative; min-height: 380px;
  display: flex; align-items: center;
  background-color: #3D5A50;
}
.cta-overlay { position: absolute; inset: 0; background: rgba(26,9,5,0.6); }
.cta-content {
  position: relative; z-index: 1;
  padding: 80px clamp(20px, 5vw, 80px);
  display: flex; flex-direction: column; align-items: flex-start; gap: 32px;
}
.cta-text { font-size: clamp(32px, 5vw, 60px); color: var(--cream); line-height: 1.1; }
.cta-text em { font-style: normal; color: var(--amber); }

@media (max-width: 768px) {
  .intro-inner, .daily-section, .events-section, .offsite-inner {
    grid-template-columns: 1fr;
  }
  .daily-photo { height: 280px; order: -1; }
  .events-photo { order: -1; height: 280px; }
  .offsite-inner { grid-template-columns: 1fr; }
}
</style>
