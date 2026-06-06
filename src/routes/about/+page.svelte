<script>
  const values = [
    { title: 'Freshness',    desc: 'Our menu changes every day based on what\'s fresh. Local fishermen and farmers tell us what\'s good, and that\'s what we cook.' },
    { title: 'Community',   desc: 'We\'ve been a part of Bodden Town for years. Our customers are our neighbours. We cook for them like family every single day.' },
    { title: 'Authenticity', desc: 'No pretend Caribbean food here. Every recipe is the real thing — passed down, time-tested, and cooked the way it\'s supposed to be.' },
    { title: 'Warmth',      desc: 'You\'ll always be welcomed with a smile. Sit on the deck, enjoy the ocean breeze, feed the tarpon, and let us take care of the rest.' },
  ];

  const milestones = [
    { year: '2010', text: 'Seaside Paradise Restaurant opens on Bodden Town Road, serving fresh local and Caribbean food to the community.',             offset: false },
    { year: '2015', text: 'Added catering and private event services. Now feeding families across Grand Cayman for celebrations and gatherings.',       offset: true  },
    { year: '2020', text: 'Expanded the back deck to seat more guests with views of the ocean. Feeding tarpon from the deck became a local tradition.', offset: false },
    { year: '2024', text: 'Recognised as one of Grand Cayman\'s best kept secrets — 4.7 stars on TripAdvisor and a loyal local following.',            offset: true  },
  ];
</script>

<svelte:head>
  <title>About Our Restaurant — Seaside Paradise</title>
</svelte:head>

<!-- ── HERO ── -->
<section class="about-hero photo-bg" style="background-image:url('/photos/about-hero.jpg')">
  <div class="hero-overlay"></div>
  <div class="hero-title-wrap">
    <h1 class="hero-title">About<br />Our<br />Restaurant</h1>
  </div>
</section>

<!-- ── STORY ── -->
<section class="story-section">
  <div class="story-inner">
    <div class="story-content">
      <div class="story-head">
        <p class="eyebrow-red">OUR STORY</p>
        <h2 class="story-title">Authentic Caribbean cooking<br />right in Bodden Town.</h2>
      </div>
      <div class="story-body">
        <p>We're a small local restaurant with a big heart. Part of the Rodneys Group, Seaside Paradise has been feeding Bodden Town — and anyone lucky enough to find us — with fresh, homestyle Caribbean food. Our back deck looks out over the water. Pull up a chair.</p>
        <p>Every morning we source from local fishermen and farmers. The menu changes daily based on what's fresh. That's how it's always been here — real ingredients, real cooking, no shortcuts.</p>
      </div>
    </div>
    <div class="story-photo photo-bg" style="background-image:url('/photos/about-story-oval.jpg')"></div>
  </div>
</section>

<!-- ── VALUES ── -->
<section class="values-section">
  <div class="values-inner">
    <div class="values-grid">
      {#each values as v}
        <div class="value-card">
          <svg class="value-icon" width="40" height="40" viewBox="0 0 40 40" fill="none" aria-hidden="true">
            <path d="M20 4V36M4 20H36M7.5 7.5L32.5 32.5M32.5 7.5L7.5 32.5" stroke="#E8973A" stroke-width="2.5" stroke-linecap="round"/>
            <circle cx="20" cy="20" r="3.5" fill="#E8973A"/>
          </svg>
          <div class="value-text">
            <h3 class="value-title">{v.title}</h3>
            <p class="value-desc">{v.desc}</p>
          </div>
        </div>
      {/each}
    </div>
    <div class="values-title-col">
      <p class="eyebrow-amber">VALUES</p>
      <h2 class="values-heading">What We<br />Believe</h2>
    </div>
  </div>
</section>

<!-- ── VIDEO ── -->
<section class="video-section photo-bg" style="background-image:url('/photos/about-video.jpg')"></section>

<!-- ── NUMBERS ── -->
<section class="numbers-section">
  <div class="numbers-inner">
    <h2 class="numbers-title">This is<br />our numbers</h2>
    <div class="numbers-row">
      <div class="number-item">
        <span class="number-val">4.7★</span>
        <span class="number-lbl">TRIPADVISOR</span>
      </div>
      <div class="number-divider"></div>
      <div class="number-item">
        <span class="number-val">91</span>
        <span class="number-lbl">REVIEWS</span>
      </div>
      <div class="number-divider"></div>
      <div class="number-item">
        <span class="number-val">7</span>
        <span class="number-lbl">DAYS A WEEK</span>
      </div>
    </div>
  </div>
</section>

<!-- ── ACHIEVEMENTS ── -->
<section class="achievements-section">
  <div class="ach-inner photo-bg" style="background-image:url('/photos/about-hero.jpg')">
    <div class="ach-overlay"></div>
    <div class="ach-content">
      <div class="ach-title-block">
        <p class="ach-eyebrow">ACHIEVEMENTS</p>
        <h2 class="ach-title">What People<br />Say</h2>
      </div>
      <div class="ach-list">
        <div class="ach-item ach-bordered">
          <span class="ach-year">2022</span>
          <div>
            <h3 class="ach-name">#1 Local Spot in Bodden Town</h3>
            <p class="ach-source">TripAdvisor Community, 2024</p>
          </div>
        </div>
        <div class="ach-item">
          <span class="ach-year">2023</span>
          <div>
            <h3 class="ach-name">Best Hidden Gem in Grand Cayman</h3>
            <p class="ach-source">Local Community Choice</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ── MILESTONES ── -->
<section class="milestones-section">
  <div class="milestones-header">
    <p class="eyebrow-red">MILESTONES</p>
    <h2 class="milestones-title">Our Journey</h2>
  </div>
  <div class="milestones-grid">
    {#each milestones as m}
      <div class="milestone" class:offset={m.offset}>
        <div class="milestone-inner">
          <span class="milestone-year">{m.year}</span>
          <p class="milestone-text">{m.text}</p>
        </div>
      </div>
    {/each}
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

/* ── HERO ── */
.about-hero {
  position: relative;
  height: 400px;
  margin-top: calc(-1 * var(--navbar-h));
  background-color: #3D5A50;
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
}

/* ── STORY ── */
.story-section {
  background: #fffff4;
  padding: var(--section-pad) clamp(24px, 5.6vw, 80px);
}
.story-inner {
  max-width: 1280px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  gap: clamp(48px, 8vw, 109px);
}
.story-content {
  display: flex;
  flex-direction: column;
  gap: 48px;
  padding-left: clamp(0px, 3vw, 40px);
  flex: 1;
  min-width: 0;
}
.story-head {
  display: flex;
  flex-direction: column;
  gap: 16px;
}
.story-title {
  font-family: var(--font-display);
  font-size: clamp(32px, 5vw, 64px);
  line-height: 1.12;
  color: var(--dark);
}
.story-body {
  display: flex;
  flex-direction: column;
  gap: 16px;
  max-width: 541px;
}
.story-body p {
  font-family: var(--font-body);
  font-size: clamp(16px, 1.5vw, 20px);
  line-height: 30px;
  color: var(--dark);
  opacity: 0.7;
}
.story-photo {
  width: clamp(240px, 30vw, 413px);
  aspect-ratio: 413 / 656;
  border-radius: 300px;
  flex-shrink: 0;
  background-color: #5A7060;
  background-size: cover;
  background-position: center;
}

/* ── VALUES ── */
.values-section {
  background: var(--bg-dark);
  padding: clamp(60px, 7vw, 100px) clamp(24px, 7vw, 100px);
}
.values-inner {
  max-width: 1280px;
  margin: 0 auto;
  display: flex;
  align-items: stretch;
  justify-content: space-between;
  gap: 40px;
}
.values-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  max-width: 846px;
  flex: 1;
}
.value-card {
  background: var(--cream);
  padding: 24px;
  display: flex;
  flex-direction: column;
  gap: 40px;
}
.value-icon { flex-shrink: 0; }
.value-text {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.value-title {
  font-family: var(--font-label);
  font-weight: 600;
  font-size: 26px;
  line-height: 32px;
  color: var(--dark);
}
.value-desc {
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 24px;
  color: var(--dark);
  opacity: 0.5;
}
.values-title-col {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-self: stretch;
  flex-shrink: 0;
  width: clamp(200px, 26vw, 334px);
}
.values-heading {
  font-family: var(--font-display);
  font-size: clamp(48px, 6.5vw, 80px);
  line-height: 1.1;
  color: var(--cream);
}

/* ── VIDEO ── */
.video-section {
  height: 620px;
  background-color: #4A7060;
  background-size: cover;
  background-position: center;
}

/* ── NUMBERS ── */
.numbers-section {
  background: #fffff4;
  padding: var(--section-pad) clamp(24px, 5.6vw, 80px);
}
.numbers-inner {
  max-width: 1280px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 40px;
}
.numbers-title {
  font-family: var(--font-display);
  font-size: clamp(36px, 5vw, 64px);
  line-height: 1.12;
  color: var(--dark);
  white-space: nowrap;
}
.numbers-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 40px;
  flex-wrap: wrap;
}
.number-item {
  display: flex;
  flex-direction: column;
  gap: 12px;
  white-space: nowrap;
}
.number-val {
  font-family: var(--font-display);
  font-size: clamp(48px, 6vw, 80px);
  line-height: 1.1;
  color: var(--amber);
}
.number-lbl {
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 24px;
  letter-spacing: 1.92px;
  color: var(--dark);
}
.number-divider {
  width: 1px;
  height: 180px;
  background: rgba(45, 26, 20, 0.2);
  flex-shrink: 0;
}

/* ── ACHIEVEMENTS ── */
.achievements-section {
  background: #fffff4;
  padding: 0 clamp(24px, 5.6vw, 80px);
}
.ach-inner {
  position: relative;
  max-width: 1280px;
  margin: 0 auto;
  padding: clamp(32px, 4.4vw, 56px) clamp(24px, 4.4vw, 64px);
  background-color: #3D5A50;
  background-size: cover;
  background-position: center;
}
.ach-overlay {
  position: absolute;
  inset: 0;
  background: rgba(26,9,5,0.55);
}
.ach-content {
  position: relative;
  z-index: 1;
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 40px;
  flex-wrap: wrap;
}
.ach-title-block {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.ach-eyebrow {
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 24px;
  letter-spacing: 1.92px;
  color: var(--cream);
}
.ach-title {
  font-family: var(--font-display);
  font-size: clamp(40px, 6vw, 80px);
  line-height: 1.1;
  color: var(--cream);
  max-width: 365px;
}
.ach-list {
  background: var(--cream);
  padding: clamp(20px, 2.2vw, 32px) clamp(20px, 2.8vw, 40px);
  display: flex;
  flex-direction: column;
  gap: 48px;
}
.ach-item {
  display: flex;
  flex-direction: column;
  gap: 6px;
}
.ach-bordered {
  padding-bottom: 48px;
  border-bottom: 2px solid rgba(45,26,20,0.2);
}
.ach-year {
  font-family: var(--font-body);
  font-weight: 600;
  font-size: 20px;
  line-height: 30px;
  color: var(--amber);
}
.ach-name {
  font-family: var(--font-label);
  font-weight: 600;
  font-size: 26px;
  line-height: 32px;
  color: var(--dark);
  white-space: nowrap;
}
.ach-source {
  font-family: var(--font-body);
  font-size: 20px;
  line-height: 30px;
  color: var(--dark);
  opacity: 0.5;
}

/* ── MILESTONES ── */
.milestones-section {
  background: #fffff4;
  padding: var(--section-pad) clamp(24px, 5.6vw, 80px);
}
.milestones-header {
  max-width: 1280px;
  margin: 0 auto 64px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  align-items: center;
  text-align: center;
}
.milestones-title {
  font-family: var(--font-display);
  font-size: clamp(48px, 6vw, 80px);
  line-height: 1.1;
  color: var(--dark);
}
.milestones-grid {
  max-width: 1280px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  align-items: start;
}
.milestone { display: flex; flex-direction: column; }
.milestone.offset { padding-top: 106px; }
.milestone-inner {
  border-left: 2px solid var(--amber);
  padding: 34px 24px 34px 40px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.milestone-year {
  font-family: var(--font-display);
  font-size: clamp(36px, 4.4vw, 64px);
  line-height: 1.12;
  color: var(--dark);
  text-align: center;
  white-space: nowrap;
}
.milestone-text {
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 24px;
  color: var(--dark);
  opacity: 0.8;
}

/* ── RESPONSIVE ── */
@media (max-width: 900px) {
  .story-inner { flex-direction: column; gap: 48px; }
  .story-content { padding-left: 0; }
  .story-photo { width: 100%; max-width: 380px; margin: 0 auto; }
  .values-inner { flex-direction: column; }
  .values-title-col { width: 100%; height: auto; flex-direction: row; justify-content: space-between; align-items: flex-end; }
  .values-heading { font-size: 52px; }
  .numbers-inner { flex-direction: column; align-items: flex-start; }
  .milestones-grid { grid-template-columns: repeat(2, 1fr); }
  .milestone.offset { padding-top: 0; }
  .ach-content { flex-direction: column; }
}

@media (max-width: 600px) {
  .about-hero { height: 320px; }
  .values-grid { grid-template-columns: 1fr; }
  .milestones-grid { grid-template-columns: 1fr; }
  .numbers-row { flex-direction: column; gap: 32px; }
  .number-divider { width: 120px; height: 1px; }
  .video-section { height: 360px; }
  .ach-name { white-space: normal; }
}
</style>
