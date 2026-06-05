<script>
  import { onMount } from 'svelte';

  const favourites = [
    { name: 'Slow-Braised\nOxtail',   price: '$12', desc: 'Tender fall-off-the-bone oxtail in rich dark gravy.' },
    { name: 'Curry\nGoat',            price: '$13', desc: 'Slow-cooked in Caribbean curry with potatoes and peppers.' },
    { name: 'Jerk\nChicken',          price: '$10', desc: 'Marinated overnight. Grilled until the skin blisters.' },
    { name: 'Brown\nStew Fish',       price: '$12', desc: 'Fresh local fish in a rich brown gravy with island spices.' },
  ];

  const values = [
    { title: 'Fresh from Local\nFishermen & Farmers Daily' },
    { title: 'Years Serving the\nBodden Town Community' },
    { title: 'Daily Rotating Menu —\nAlways Fresh, Never Frozen' },
  ];

  const specials = [
    { name: 'Rondon', desc: 'A true Caymanian classic. Salt fish slow-cooked in coconut milk with breadfruit and ground provisions. Ask for it when it\'s on.' },
    { name: 'Brown Stew Fish', desc: 'Fresh local fish braised low and slow in a rich brown gravy with peppers, onions and island spices. A firm favourite.' },
    { name: 'Jerk Chicken', desc: 'Marinated overnight in scotch bonnet, allspice and thyme, then cooked over open heat until the skin blisters and the inside stays juicy.' },
    { name: 'Oxtail', desc: 'Slow-braised for hours until fall-off-the-bone tender. Served with rice and peas. Our most-ordered dish — and for good reason.' },
  ];

  const faqs = [
    { q: 'How can I make a reservation?', a: 'No reservations needed. Walk in any time between 11am and 10:30pm. We\'ll find you a seat.' },
    { q: 'Do you offer catering or private events?', a: 'Yes! We cater events across Grand Cayman and host private events at the restaurant. Call us to discuss.' },
    { q: 'What is the dress code?', a: 'Come as you are — shorts, flip flops, whatever you\'re wearing. We\'re a laid-back island spot and everyone is welcome.' },
    { q: 'Can I find Seaside Paradise on social media?', a: 'Yes! Follow us @seasideparadiserestaurant on Instagram and @seasideparadisefood on TikTok.' },
    { q: 'What are the opening hours?', a: 'We\'re open Monday through Sunday, 11:00 AM to 10:30 PM. Open every day of the year.' },
  ];

  let openFaq = null;
  function toggleFaq(i) { openFaq = openFaq === i ? null : i; }

  const testimonials = [
    { quote: '"Best homemade food I\'ve found on the island. Fresh fish, jerk chicken, oxtail — everything was incredible. The vibe is pure Cayman and the portions are generous."', author: 'Sarah M.', source: 'TripAdvisor' },
    { quote: '"Hidden gem in Bodden Town. Oxtail melts off the bone and the view from the back deck over the water is absolutely priceless."', author: 'Tricia W.', source: 'TripAdvisor' },
    { quote: '"The jerk chicken is the real deal — scotch bonnet heat, smoky char, fall-off-the-bone tender. Best plate on the island."', author: 'Marcus L.', source: 'Google' },
  ];
  let activeTestimonial = 0;

  const blogs = [
    { date: '03 FEB 2024', title: 'Rondon: The Original Caymanian One-Pot Wonder', excerpt: 'The dish that defines Caribbean soul food — and why we make it every Friday at Seaside Paradise.' },
    { date: '05 APR 2024', title: 'Sunday Conch Soup — A Bodden Town Tradition', excerpt: 'Every Sunday morning starts with a massive pot of conch soup. Here\'s how it comes together.' },
  ];
</script>

<svelte:head>
  <title>Seaside Paradise Restaurant — Real Caribbean Food, Bodden Town</title>
</svelte:head>

<!-- ── HERO ─────────────────────────────────────────────────────── -->
<section class="hero photo-bg">
  <div class="hero-overlay"></div>
  <div class="hero-content">
    <h1 class="display hero-title">Real Caribbean Food.<br />Bodden Town Born.</h1>
    <p class="hero-sub">Fresh local and Caribbean dishes cooked every day at our waterfront spot in the heart of Bodden Town, Grand Cayman.</p>
    <a href="/menu" class="btn btn-outline-cream">See Today's Menu</a>
  </div>
</section>

<!-- ── CATEGORIES ──────────────────────────────────────────────── -->
<section class="categories-section">
  <div class="categories-inner">
    <div class="cat-left">
      <span class="label">Categories</span>
      <div class="cat-words">
        {#each ['Soups', 'Mains', 'Grills', 'Sides'] as word, i}
          <span class="cat-word">{word}</span>
          {#if i < 3}<span class="cat-divider">—</span>{/if}
        {/each}
      </div>
      <p class="cat-desc">From oxtail and curry goat to jerk chicken and conch soup — every dish is slow-cooked, well-seasoned, and made the way it's supposed to be. Ask us what's hot today when you walk in.</p>
      <a href="/menu" class="cat-link">See All Menu →</a>
    </div>
    <div class="cat-right photo-bg" style="background-image:url('/photos/restaurant-exterior.jpg')"></div>
  </div>
</section>

<!-- ── STORY / ABOUT ───────────────────────────────────────────── -->
<section class="story-section photo-bg" style="background-image:url('/photos/beach-deck.jpg')">
  <div class="story-overlay"></div>
  <div class="story-content">
    <h2 class="display story-title">The Real<br />Taste of<br />Grand Cayman</h2>
    <p class="story-body">We cook fresh every day. Our menu follows the catch — whatever the fishermen bring in and local farms provide that morning is what ends up on your plate. No shortcuts. Just real Caribbean cooking.</p>
  </div>
</section>

<!-- ── ISLAND FAVOURITES ───────────────────────────────────────── -->
<section class="favourites-section">
  <div class="container">
    <span class="label">Crowd Favourites</span>
    <h2 class="display section-title">Island Favourites</h2>
    <div class="favourites-grid">
      {#each favourites as item}
        <div class="fav-card">
          <div class="fav-photo photo-bg"></div>
          <div class="fav-info">
            <div class="fav-name-row">
              <h3 class="fav-name">{item.name.replace('\n', ' ')}</h3>
              <span class="fav-price">{item.price}</span>
            </div>
            <p class="fav-desc">{item.desc}</p>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- ── OUR VALUES ─────────────────────────────────────────────── -->
<section class="values-section">
  <div class="values-left photo-bg" style="background-image:url('/photos/restaurant-patio.jpg')">
    <div class="values-photo-overlay"></div>
  </div>
  <div class="values-right">
    <span class="label">Our Story</span>
    <h2 class="display">Our Values</h2>
    <p class="values-sub">Simple ingredients. Big flavors. Genuine warmth. That's what Seaside Paradise is built on.</p>
    <ul class="values-list">
      {#each values as v}
        <li>
          <span class="value-dot"></span>
          <span>{v.title}</span>
        </li>
      {/each}
    </ul>
  </div>
</section>

<!-- ── SPECIALS ───────────────────────────────────────────────── -->
<section class="specials-section">
  <div class="container">
    <div class="specials-header">
      <span class="label">Today's Specials</span>
      <h2 class="display specials-title">Rondon &amp; Brown Stew Fish</h2>
    </div>
    <div class="specials-grid">
      {#each specials as item}
        <div class="special-item">
          <h3 class="special-name">{item.name}</h3>
          <p class="special-desc">{item.desc}</p>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- ── CTA BANNER ─────────────────────────────────────────────── -->
<section class="cta-banner photo-bg" style="background-image:url('/photos/beach-trees.jpg')">
  <div class="cta-overlay"></div>
  <div class="cta-content">
    <h2 class="display cta-text">Good food,<br /><em>good vibes,</em><br />every day.</h2>
    <div class="cta-buttons">
      <a href="/contact" class="btn btn-outline-cream">Make A Reservation</a>
      <a href="/contact" class="btn btn-outline-cream">Check Location</a>
    </div>
  </div>
</section>

<!-- ── FAQ ──────────────────────────────────────────────────────── -->
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

<!-- ── TESTIMONIALS ───────────────────────────────────────────── -->
<section class="testimonials-section">
  <div class="container">
    <span class="label">Testimonials</span>
    <h2 class="display testimonials-title">What People Say</h2>
    <div class="amber-line"></div>
    <blockquote class="testimonial-quote">
      {testimonials[activeTestimonial].quote}
    </blockquote>
    <p class="testimonial-author">
      {testimonials[activeTestimonial].author} — {testimonials[activeTestimonial].source} ★★★★★
    </p>
    <div class="testimonial-dots">
      {#each testimonials as _, i}
        <button
          class="dot"
          class:active={i === activeTestimonial}
          on:click={() => activeTestimonial = i}
          aria-label="Testimonial {i + 1}"
        ></button>
      {/each}
    </div>
  </div>
</section>

<!-- ── BLOG ──────────────────────────────────────────────────── -->
<section class="blog-section">
  <div class="container">
    <span class="label">Blog</span>
    <h2 class="display">Island Stories</h2>
    <div class="blog-grid">
      {#each blogs as post}
        <article class="blog-card">
          <div class="blog-photo photo-bg"></div>
          <div class="blog-body">
            <span class="blog-date label">{post.date}</span>
            <h3 class="blog-title">{post.title}</h3>
            <p class="blog-excerpt">{post.excerpt}</p>
            <a href="/blog" class="blog-link">Read More →</a>
          </div>
        </article>
      {/each}
    </div>
  </div>
</section>

<style>
/* HERO */
.hero {
  position: relative;
  min-height: 100svh;
  display: flex;
  align-items: flex-end;
  background-color: #3D5A50;
  background-image: url('/photos/hero.jpg');
}
.hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(26,9,5,0.85) 0%, rgba(26,9,5,0.3) 60%, transparent 100%);
}
.hero-content {
  position: relative;
  z-index: 1;
  max-width: var(--container);
  width: 100%;
  margin: 0 auto;
  padding: 0 clamp(20px, 5vw, 80px) clamp(60px, 8vw, 120px);
}
.hero-title {
  font-size: clamp(40px, 7vw, 90px);
  color: var(--cream);
  line-height: 1.05;
  margin-bottom: 20px;
  text-shadow: 0 2px 20px rgba(0,0,0,0.4);
}
.hero-sub {
  max-width: 480px;
  font-size: clamp(15px, 2vw, 17px);
  color: rgba(247,240,220,0.85);
  margin-bottom: 32px;
  line-height: 1.6;
}

/* CATEGORIES */
.categories-section { background: var(--cream); }
.categories-inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  min-height: 560px;
}
.cat-left {
  padding: clamp(48px, 6vw, 96px) clamp(32px, 5vw, 80px);
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 20px;
}
.cat-words {
  display: flex;
  flex-direction: column;
}
.cat-word {
  font-family: var(--font-display);
  font-size: clamp(36px, 5vw, 64px);
  color: var(--dark);
  line-height: 1.1;
}
.cat-divider {
  font-size: 20px;
  color: var(--amber);
  margin: -4px 0;
  font-family: var(--font-display);
}
.cat-desc {
  font-size: 15px;
  color: var(--text-muted);
  line-height: 1.7;
  max-width: 380px;
}
.cat-link {
  color: var(--red);
  font-size: 14px;
  font-weight: 600;
  font-family: var(--font-label);
  letter-spacing: 0.04em;
  transition: opacity 0.2s;
}
.cat-link:hover { opacity: 0.7; }
.cat-right {
  background-color: #5A7060;
  background-size: cover;
  background-position: center;
}

/* STORY */
.story-section {
  position: relative;
  min-height: 500px;
  display: flex;
  align-items: center;
  background-color: #3D5A50;
}
.story-overlay {
  position: absolute;
  inset: 0;
  background: rgba(26,9,5,0.55);
}
.story-content {
  position: relative;
  z-index: 1;
  max-width: var(--container);
  width: 100%;
  margin: 0 auto;
  padding: var(--section-pad) clamp(20px, 5vw, 80px);
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 48px;
  align-items: center;
}
.story-title {
  font-size: clamp(36px, 5vw, 64px);
  color: var(--cream);
  text-shadow: 0 2px 12px rgba(0,0,0,0.3);
}
.story-body {
  font-size: clamp(15px, 2vw, 17px);
  color: rgba(247,240,220,0.85);
  line-height: 1.7;
}

/* FAVOURITES */
.favourites-section {
  background: var(--offwhite);
  padding: var(--section-pad) 0;
}
.section-title {
  font-size: clamp(36px, 5vw, 64px);
  margin: 8px 0 48px;
}
.favourites-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 24px;
}
.fav-card {
  display: flex;
  flex-direction: column;
  background: var(--cream);
  border-radius: var(--radius);
  overflow: hidden;
  transition: transform 0.2s;
}
.fav-card:hover { transform: translateY(-4px); }
.fav-photo {
  height: 240px;
  background-color: #7A9080;
  flex-shrink: 0;
}
.fav-info { padding: 20px 16px; }
.fav-name-row { display: flex; justify-content: space-between; align-items: flex-start; gap: 8px; margin-bottom: 8px; }
.fav-name { font-family: var(--font-label); font-weight: 600; font-size: 18px; line-height: 1.3; }
.fav-price { font-family: var(--font-label); font-size: 15px; color: var(--text-muted); flex-shrink: 0; }
.fav-desc { font-size: 13px; color: var(--text-muted); line-height: 1.6; }

/* VALUES */
.values-section {
  display: grid;
  grid-template-columns: 1fr 1fr;
  min-height: 520px;
}
.values-left {
  position: relative;
  background-color: #5A7060;
  background-size: cover;
  background-position: center;
}
.values-photo-overlay {
  position: absolute;
  inset: 0;
  background: rgba(26,9,5,0.2);
}
.values-right {
  background: var(--offwhite);
  padding: clamp(48px, 6vw, 96px) clamp(40px, 5vw, 80px);
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 16px;
}
.values-right h2 { font-size: clamp(28px, 4vw, 48px); }
.values-sub { font-size: 15px; color: var(--text-muted); line-height: 1.7; max-width: 360px; }
.values-list { list-style: none; display: flex; flex-direction: column; gap: 16px; margin-top: 8px; }
.values-list li { display: flex; align-items: flex-start; gap: 12px; font-size: 15px; font-weight: 600; line-height: 1.4; }
.value-dot {
  width: 8px; height: 8px; border-radius: 50%;
  background: var(--amber); flex-shrink: 0; margin-top: 6px;
}

/* SPECIALS */
.specials-section {
  background: var(--cream);
  padding: var(--section-pad) 0;
}
.specials-header { margin-bottom: 48px; }
.specials-title { font-size: clamp(32px, 4vw, 56px); margin-top: 8px; }
.specials-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 32px 48px;
}
.special-item { border-top: 2px solid var(--amber); padding-top: 20px; }
.special-name { font-family: var(--font-label); font-weight: 600; font-size: 20px; margin-bottom: 10px; }
.special-desc { font-size: 14px; color: var(--text-muted); line-height: 1.7; }

/* CTA BANNER */
.cta-banner {
  position: relative;
  min-height: 420px;
  display: flex;
  align-items: center;
  background-color: #3D5A50;
}
.cta-overlay {
  position: absolute; inset: 0;
  background: rgba(26,9,5,0.55);
}
.cta-content {
  position: relative; z-index: 1;
  max-width: var(--container); width: 100%;
  margin: 0 auto;
  padding: 80px clamp(20px, 5vw, 80px);
  display: flex; flex-direction: column; align-items: flex-start; gap: 32px;
}
.cta-text {
  font-size: clamp(36px, 6vw, 72px);
  color: var(--cream);
  line-height: 1.1;
}
.cta-text em { font-style: normal; color: var(--amber); }
.cta-buttons { display: flex; gap: 16px; flex-wrap: wrap; }

/* FAQ */
.faq-section {
  background: var(--offwhite);
  padding: var(--section-pad) 0;
}
.faq-inner {
  display: grid;
  grid-template-columns: 1fr 1.4fr;
  gap: 80px;
  align-items: start;
}
.faq-left h2 { font-size: clamp(32px, 4vw, 52px); margin-top: 8px; }
.faq-right { display: flex; flex-direction: column; }
.faq-item { }
.faq-q {
  width: 100%;
  display: flex; align-items: center; justify-content: space-between; gap: 16px;
  padding: 20px 0;
  font-family: var(--font-display);
  font-size: clamp(18px, 2.5vw, 22px);
  color: var(--dark);
  text-align: left;
  transition: color 0.2s;
}
.faq-q:hover { color: var(--red); }
.faq-icon { flex-shrink: 0; transition: transform 0.3s; }
.faq-icon.open { transform: rotate(180deg); }
.faq-a {
  padding-bottom: 20px;
  font-size: 15px;
  color: var(--text-muted);
  line-height: 1.7;
}
.faq-divider { height: 1px; background: var(--border); }

/* TESTIMONIALS */
.testimonials-section {
  background: var(--bg-dark);
  padding: var(--section-pad) 0;
  text-align: left;
}
.testimonials-section .label { display: block; margin-bottom: 8px; }
.testimonials-title { font-size: clamp(32px, 5vw, 56px); color: var(--cream); margin-bottom: 24px; }
.testimonials-section .amber-line { margin-bottom: 32px; }
.testimonial-quote {
  font-size: clamp(16px, 2vw, 20px);
  color: var(--cream);
  line-height: 1.7;
  max-width: 720px;
  font-style: italic;
  margin-bottom: 20px;
}
.testimonial-author {
  font-family: var(--font-label);
  font-weight: 600;
  font-size: 14px;
  color: var(--amber);
  margin-bottom: 32px;
}
.testimonial-dots { display: flex; gap: 8px; }
.dot {
  width: 10px; height: 10px; border-radius: 50%;
  background: rgba(255,255,255,0.3);
  transition: background 0.2s, transform 0.2s;
}
.dot.active { background: var(--amber); transform: scale(1.2); }

/* BLOG */
.blog-section {
  background: var(--cream);
  padding: var(--section-pad) 0;
}
.blog-section h2 { font-size: clamp(32px, 5vw, 52px); margin: 8px 0 48px; }
.blog-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 32px; }
.blog-card {
  background: var(--offwhite);
  border-radius: var(--radius);
  overflow: hidden;
  transition: transform 0.2s;
}
.blog-card:hover { transform: translateY(-4px); }
.blog-photo { height: 220px; background-color: #7A9080; }
.blog-body { padding: 24px; }
.blog-date { display: block; color: var(--amber); margin-bottom: 10px; }
.blog-title { font-family: var(--font-label); font-weight: 600; font-size: 18px; line-height: 1.3; margin-bottom: 10px; }
.blog-excerpt { font-size: 14px; color: var(--text-muted); line-height: 1.7; margin-bottom: 16px; }
.blog-link { font-size: 13px; font-weight: 600; color: var(--red); }

/* ── RESPONSIVE ──────────────────────────────────────────────── */
@media (max-width: 1024px) {
  .favourites-grid { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 768px) {
  .categories-inner { grid-template-columns: 1fr; }
  .cat-right { height: 300px; }

  .story-content { grid-template-columns: 1fr; }

  .favourites-grid { grid-template-columns: repeat(2, 1fr); gap: 16px; }
  .fav-photo { height: 180px; }

  .values-section { grid-template-columns: 1fr; }
  .values-left { height: 300px; }

  .specials-grid { grid-template-columns: 1fr; }

  .faq-inner { grid-template-columns: 1fr; gap: 40px; }

  .blog-grid { grid-template-columns: 1fr; }
}

@media (max-width: 480px) {
  .favourites-grid { grid-template-columns: 1fr; }
  .hero-title { font-size: 36px; }
  .cta-buttons { flex-direction: column; }
  .cta-buttons .btn { width: 100%; text-align: center; justify-content: center; }
}
</style>
