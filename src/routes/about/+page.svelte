<script>
  const values = [
    { title: 'Freshness', desc: 'Our menu changes every day based on what\'s fresh. Local fishermen and farmers tell us what\'s good, and that\'s what we cook.' },
    { title: 'Community', desc: 'We\'ve been a part of Bodden Town for years. Our customers are our neighbours. We cook for them like family every single day.' },
    { title: 'Authenticity', desc: 'No pretend Caribbean food here. Every recipe is the real thing — passed down, time-tested, and cooked the way it\'s supposed to be.' },
    { title: 'Warmth', desc: 'You\'ll always be welcomed with a smile. Sit on the deck, enjoy the ocean breeze, feed the tarpon, and let us take care of the rest.' },
  ];

  const team = [
    { name: 'Chef Rodney', role: 'Head Chef & Owner' },
    { name: 'Miss Delroy', role: 'Kitchen Lead' },
    { name: 'Junior', role: 'Prep & Grill' },
    { name: 'Marcus', role: 'Grill Master' },
    { name: 'Sandra', role: 'Front of House' },
  ];

  const stats = [
    { value: '4.7★', label: 'TripAdvisor' },
    { value: '91', label: 'Reviews' },
    { value: '7', label: 'Days a Week' },
  ];

  const milestones = [
    { year: '2010', text: 'Seaside Paradise Restaurant opens on Bodden Town Road, serving fresh local and Caribbean food to the community.' },
    { year: '2015', text: 'Added catering and private event services. Now feeding families across Grand Cayman for celebrations and gatherings.' },
    { year: '2020', text: 'Expanded the back deck to seat more guests with views of the ocean. Feeding tarpon from the deck became a local tradition.' },
    { year: '2024', text: 'Recognised as one of Grand Cayman\'s best kept secrets — 4.7 stars on TripAdvisor and a loyal local following.' },
  ];
</script>

<svelte:head>
  <title>About — Seaside Paradise Restaurant</title>
</svelte:head>

<!-- ── HERO ───────────────────────────────────────────────────── -->
<section class="about-hero photo-bg" style="background-image:url('/photos/about-hero.jpg')">
  <div class="hero-overlay"></div>
  <div class="hero-content container">
    <h1 class="display hero-title">About<br />Our<br />Restaurant</h1>
  </div>
</section>

<!-- ── STORY ──────────────────────────────────────────────────── -->
<section class="story-section">
  <div class="container story-inner">
    <div class="story-text">
      <span class="label">Our Story</span>
      <h2 class="display story-title">Authentic Caribbean cooking right in Bodden Town.</h2>
      <p>We're a small local restaurant with a big heart. Part of the Rodneys Group, Seaside Paradise has been feeding Bodden Town — and anyone lucky enough to find us — with fresh, homestyle Caribbean food. Our back deck looks out over the water. Pull up a chair.</p>
      <p>Every morning we source from local fishermen and farmers. The menu changes daily based on what's fresh. That's how it's always been here — real ingredients, real cooking, no shortcuts.</p>
    </div>
    <div class="story-photo photo-bg" style="background-image:url('/photos/story-circular.jpg')"></div>
  </div>
</section>

<!-- ── VALUES ─────────────────────────────────────────────────── -->
<section class="values-section">
  <div class="values-cards">
    {#each values as v}
      <div class="value-card">
        <div class="value-accent"></div>
        <span class="value-icon">◆</span>
        <h3>{v.title}</h3>
        <p>{v.desc}</p>
      </div>
    {/each}
  </div>
  <div class="values-label-block">
    <span class="label">Values</span>
    <h2 class="display values-title">What We<br />Believe</h2>
  </div>
</section>

<!-- ── TEAM ───────────────────────────────────────────────────── -->
<section class="team-section">
  <div class="container">
    <span class="label">Team</span>
    <h2 class="display team-heading">Our Island Crew</h2>
    <p class="team-sub">A family business built on the Rodneys' passion for feeding their community with real Caribbean cooking.</p>
    <div class="team-grid">
      {#each team as member}
        <div class="team-card">
          <div class="team-photo photo-bg"></div>
          <div class="team-info">
            <h3 class="team-name">{member.name}</h3>
            <p class="team-role">{member.role}</p>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- ── STATS ──────────────────────────────────────────────────── -->
<section class="stats-section">
  <div class="container stats-inner">
    <span class="label">By the Numbers</span>
    <h2 class="display">This is our numbers</h2>
    <div class="stats-grid">
      {#each stats as s}
        <div class="stat-item">
          <span class="stat-value">{s.value}</span>
          <span class="stat-label">{s.label}</span>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- ── ACHIEVEMENTS ────────────────────────────────────────────── -->
<section class="achievements-section">
  <div class="container achievements-inner">
    <div class="ach-left">
      <span class="label">Achievements</span>
      <h2 class="display ach-title">What People Say</h2>
    </div>
    <div class="ach-right">
      <div class="ach-item">
        <span class="ach-year">2022</span>
        <div>
          <p class="ach-title-text">#1 Local Spot in Bodden Town</p>
          <p class="ach-source">TripAdvisor Community, 2024</p>
        </div>
      </div>
      <div class="ach-item">
        <span class="ach-year">2023</span>
        <div>
          <p class="ach-title-text">Best Hidden Gem in Grand Cayman</p>
          <p class="ach-source">Local Community Choice</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ── MILESTONES / JOURNEY ───────────────────────────────────── -->
<section class="milestones-section">
  <div class="container">
    <span class="label">Milestones</span>
    <h2 class="display">Our Journey</h2>
    <div class="timeline">
      {#each milestones as m}
        <div class="timeline-item">
          <span class="timeline-year">{m.year}</span>
          <div class="timeline-dot"></div>
          <p class="timeline-text">{m.text}</p>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
/* HERO */
.about-hero {
  position: relative;
  height: 500px;
  display: flex;
  align-items: flex-end;
  background-color: #3D5A50;
}
.hero-overlay { position: absolute; inset: 0; background: rgba(26,9,5,0.55); }
.hero-content { position: relative; z-index: 1; padding-bottom: 64px; }
.hero-title { font-size: clamp(40px, 7vw, 80px); color: var(--cream); line-height: 1.0; }

/* STORY */
.story-section { background: var(--offwhite); padding: var(--section-pad) 0; }
.story-inner {
  display: grid; grid-template-columns: 1fr 380px; gap: 80px; align-items: center;
}
.story-text { display: flex; flex-direction: column; gap: 20px; }
.story-text .label { display: block; }
.story-title { font-size: clamp(28px, 4vw, 44px); margin: 8px 0 16px; }
.story-text p { font-size: 16px; color: var(--text-muted); line-height: 1.8; }
.story-photo {
  width: 100%;
  aspect-ratio: 1;
  border-radius: 50%;
  overflow: hidden;
  background-color: #5A7060;
}

/* VALUES */
.values-section {
  background: var(--bg-dark);
  display: grid;
  grid-template-columns: 2fr 1fr;
  min-height: 560px;
}
.values-cards {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0;
}
.value-card {
  background: var(--offwhite);
  padding: 36px 28px;
  border: 1px solid rgba(247,240,220,0.1);
  display: flex; flex-direction: column; gap: 12px;
  position: relative;
  overflow: hidden;
}
.value-accent { position: absolute; top: 0; left: 0; right: 0; height: 4px; background: var(--amber); }
.value-icon { font-size: 18px; color: var(--amber); }
.value-card h3 { font-family: var(--font-label); font-weight: 600; font-size: 17px; }
.value-card p { font-size: 14px; color: var(--text-muted); line-height: 1.7; }

.values-label-block {
  display: flex; flex-direction: column;
  justify-content: flex-end;
  padding: clamp(32px, 4vw, 64px);
  gap: 16px;
}
.values-title { font-size: clamp(40px, 5vw, 64px); color: var(--cream); line-height: 1.0; }

/* TEAM */
.team-section { background: var(--cream); padding: var(--section-pad) 0; }
.team-heading { font-size: clamp(32px, 4vw, 52px); margin: 8px 0 12px; }
.team-sub { font-size: 16px; color: var(--text-muted); margin-bottom: 48px; max-width: 480px; }
.team-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 20px;
}
.team-card { display: flex; flex-direction: column; gap: 12px; }
.team-photo { height: 180px; border-radius: var(--radius); background-color: #8A9E90; }
.team-name { font-family: var(--font-label); font-weight: 600; font-size: 15px; }
.team-role { font-size: 13px; color: var(--text-muted); }

/* STATS */
.stats-section { background: var(--offwhite); padding: var(--section-pad) 0; }
.stats-inner { display: flex; flex-direction: column; gap: 40px; }
.stats-inner h2 { font-size: clamp(28px, 4vw, 44px); }
.stats-grid { display: flex; gap: 64px; flex-wrap: wrap; }
.stat-item { display: flex; flex-direction: column; gap: 6px; }
.stat-value { font-family: var(--font-display); font-size: clamp(40px, 5vw, 64px); color: var(--dark); }
.stat-label { font-family: var(--font-label); font-size: 12px; letter-spacing: 0.1em; text-transform: uppercase; color: var(--amber); }

/* ACHIEVEMENTS */
.achievements-section { background: var(--cream); padding: var(--section-pad) 0; }
.achievements-inner { display: grid; grid-template-columns: 1fr 2fr; gap: 80px; align-items: start; }
.ach-title { font-size: clamp(28px, 4vw, 44px); margin-top: 8px; }
.ach-right { display: flex; flex-direction: column; gap: 32px; }
.ach-item { display: flex; gap: 32px; align-items: flex-start; }
.ach-year { font-family: var(--font-label); font-weight: 600; font-size: 14px; color: var(--amber); white-space: nowrap; padding-top: 3px; }
.ach-title-text { font-family: var(--font-label); font-weight: 600; font-size: 18px; margin-bottom: 4px; }
.ach-source { font-size: 14px; color: var(--text-muted); }

/* MILESTONES */
.milestones-section { background: var(--offwhite); padding: var(--section-pad) 0; }
.milestones-section .label { display: block; margin-bottom: 8px; }
.milestones-section h2 { font-size: clamp(28px, 4vw, 44px); margin-bottom: 56px; }
.timeline { display: grid; grid-template-columns: repeat(4, 1fr); gap: 32px; position: relative; }
.timeline::before {
  content: '';
  position: absolute;
  top: 16px; left: 0; right: 0;
  height: 1px; background: var(--amber);
}
.timeline-item { display: flex; flex-direction: column; gap: 16px; padding-top: 40px; position: relative; }
.timeline-dot {
  position: absolute; top: 8px; left: 0;
  width: 16px; height: 16px; border-radius: 50%;
  background: var(--amber); border: 3px solid var(--offwhite);
}
.timeline-year { font-family: var(--font-label); font-weight: 600; font-size: 28px; color: var(--dark); }
.timeline-text { font-size: 14px; color: var(--text-muted); line-height: 1.7; }

/* RESPONSIVE */
@media (max-width: 1024px) {
  .team-grid { grid-template-columns: repeat(3, 1fr); }
  .timeline { grid-template-columns: repeat(2, 1fr); }
  .timeline::before { display: none; }
}
@media (max-width: 768px) {
  .story-inner { grid-template-columns: 1fr; }
  .story-photo { width: 240px; height: 240px; margin: 0 auto; }
  .values-section { grid-template-columns: 1fr; }
  .values-label-block { padding: 40px 24px; }
  .achievements-inner { grid-template-columns: 1fr; gap: 32px; }
  .team-grid { grid-template-columns: repeat(2, 1fr); }
  .stats-grid { gap: 40px; }
}
@media (max-width: 480px) {
  .timeline { grid-template-columns: 1fr; }
  .team-grid { grid-template-columns: repeat(2, 1fr); }
  .values-cards { grid-template-columns: 1fr; }
}
</style>
