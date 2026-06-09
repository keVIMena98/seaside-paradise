<script>
  import { slide, fade } from 'svelte/transition';
  import SEO from '$lib/components/SEO.svelte';

  const homeSchema = [
    {
      "@context": "https://schema.org",
      "@type": "FAQPage",
      "mainEntity": [
        {
          "@type": "Question",
          "name": "Do I need a reservation at Seaside Paradise Restaurant?",
          "acceptedAnswer": { "@type": "Answer", "text": "No reservations needed. Walk in any time between 11am and 9:30pm. We'll find you a seat." }
        },
        {
          "@type": "Question",
          "name": "What are the opening hours of Seaside Paradise Restaurant?",
          "acceptedAnswer": { "@type": "Answer", "text": "Seaside Paradise Restaurant is open Monday through Sunday, 11:00 AM to 9:30 PM, every day of the year." }
        },
        {
          "@type": "Question",
          "name": "Does Seaside Paradise offer catering?",
          "acceptedAnswer": { "@type": "Answer", "text": "Yes! We cater events across Grand Cayman and host private events at the restaurant. Call +1 (345) 516-4367 to discuss." }
        },
        {
          "@type": "Question",
          "name": "Where is Seaside Paradise Restaurant located?",
          "acceptedAnswer": { "@type": "Answer", "text": "238 Bodden Town Road, Bodden Town, Grand Cayman, KY2-2500, Cayman Islands." }
        },
        {
          "@type": "Question",
          "name": "What type of food does Seaside Paradise serve?",
          "acceptedAnswer": { "@type": "Answer", "text": "Authentic Caribbean and Caymanian cuisine — jerk chicken, oxtail, curry goat, brown stew fish, rondon, conch soup, and fresh local seafood cooked daily." }
        }
      ]
    },
    {
      "@context": "https://schema.org",
      "@type": "BreadcrumbList",
      "itemListElement": [
        { "@type": "ListItem", "position": 1, "name": "Home", "item": "https://seasideparadise.ky/" }
      ]
    }
  ];

  // Scroll-reveal action
  function reveal(node, { delay = 0, y = 28 } = {}) {
    node.style.cssText += `opacity:0;transform:translateY(${y}px);transition:opacity .7s ${delay}ms cubic-bezier(.4,0,.2,1),transform .7s ${delay}ms cubic-bezier(.4,0,.2,1)`;
    const obs = new IntersectionObserver(([e]) => {
      if (e.isIntersecting) {
        node.style.opacity = '1';
        node.style.transform = 'translateY(0)';
        obs.disconnect();
      }
    }, { threshold: 0.12, rootMargin: '0px 0px -48px 0px' });
    obs.observe(node);
    return { destroy: () => obs.disconnect() };
  }

  const favourites = [
    { name: ['Slow-Braised', 'Oxtail'],  price: '$12', img: '/photos/dish-oxtail.jpg' },
    { name: ['Curry', 'Goat'],           price: '$13', img: '/photos/dish-curry-goat.jpg' },
    { name: ['Jerk', 'Chicken'],         price: '$10', img: '/photos/dish-jerk-chicken.jpg' },
    { name: ['Brown', 'Stew Fish'],      price: '$12', img: '/photos/dish-brown-stew-fish.jpg' },
  ];

  const values = [
    'Fresh from Local Fishermen & Farmers Daily',
    'Years Serving the Bodden Town Community',
    'Daily Rotating Menu — Always Fresh, Never Frozen',
  ];

  const specialsLeft = [
    { name: 'Rondon',          desc: "A true Caymanian classic. Salt fish slow-cooked in coconut milk with breadfruit and ground provisions. Ask for it when it's on." },
    { name: 'Brown Stew Fish', desc: 'Fresh local fish braised low and slow in a rich brown gravy with peppers, onions and island spices. A firm favourite.' },
  ];
  const specialsRight = [
    { name: 'Jerk Chicken', desc: 'Marinated overnight in scotch bonnet, allspice and thyme, then cooked over open heat until the skin blisters and the inside stays juicy.' },
    { name: 'Oxtail',       desc: 'Slow-braised for hours until fall-off-the-bone tender. Served with rice and peas. Our most-ordered dish — and for good reason.' },
  ];

  const faqs = [
    { q: 'How can I make a reservation?',             a: "No reservations needed. Walk in any time between 11am and 9:30pm. We'll find you a seat." },
    { q: 'Do you offer catering or private events?',  a: 'Yes! We cater events across Grand Cayman and host private events at the restaurant. Call us to discuss.' },
    { q: 'What is the dress code?',                   a: "Come as you are — shorts, flip flops, whatever you're wearing. We're a laid-back island spot and everyone is welcome at our table." },
    { q: 'Can I find Seaside Paradise on social media?', a: 'Yes! Follow us @seasideparadiserestaurant on Instagram and @seasideparadisefood on TikTok.' },
    { q: 'What are the opening hours?',               a: "We're open Monday through Sunday, 11:00 AM to 9:30 PM. Open every day of the year." },
  ];
  let openFaq = 2;
  function toggleFaq(i) { openFaq = openFaq === i ? null : i; }

  const testimonials = [
    { quote: '"Best homemade food I\'ve found on the island. Fresh fish, jerk chicken, oxtail — everything was incredible. The vibe is pure Cayman and the portions are generous. Will be back every time I visit."', author: 'Sarah M. — TripAdvisor ★★★★★', photo: '/photos/testimonials-photo.jpg' },
    { quote: '"Hidden gem in Bodden Town. Oxtail melts off the bone and the view from the back deck over the water is absolutely priceless."',                                                                      author: 'Tricia W. — TripAdvisor ★★★★★', photo: '/photos/categories.jpg' },
    { quote: '"The jerk chicken is the real deal — scotch bonnet heat, smoky char, fall-off-the-bone tender. Best plate on the island."',                                                                          author: 'Marcus L. — Google ★★★★★',     photo: '/photos/values-bg.jpg' },
  ];
  let activeTestimonial = 0;
  function prevTestimonial() { activeTestimonial = (activeTestimonial - 1 + testimonials.length) % testimonials.length; }
  function nextTestimonial() { activeTestimonial = (activeTestimonial + 1) % testimonials.length; }
</script>

<SEO
  title="Seaside Paradise Restaurant — Real Caribbean Food, Bodden Town, Grand Cayman"
  description="The best Caribbean restaurant in Grand Cayman. Jerk chicken, oxtail, curry goat, brown stew fish and authentic Caymanian cooking served fresh every day on our waterfront terrace in Bodden Town. Open 11am–9:30pm daily."
  canonical="/"
  image="https://seasideparadise.ky/photos/hero.jpg"
  jsonLd={homeSchema}
/>

<!-- ── HERO ─────────────────────────────────────────────────────── -->
<section class="hero">
  <div class="hero-content">
    <h1 class="display hero-title">Real Caribbean Food.<br />Bodden Town Born.</h1>
    <p class="hero-sub">Fresh local and Caribbean dishes cooked every day at our waterfront spot in the heart of Bodden Town, Grand Cayman.</p>
    <a href="/menu" class="btn-pill-cream">See Today's Menu</a>
  </div>
  <div class="scroll-hint" aria-hidden="true">
    <span></span>
  </div>
</section>

<!-- ── CATEGORIES ──────────────────────────────────────────────── -->
<section class="categories-section">
  <div class="categories-inner">
    <div class="cat-left" use:reveal>
      <div>
        <p class="label lbl-red">CATEGORIES</p>
        <div class="cat-list">
          <span class="cat-word">Soups</span>
          <span class="cat-word">Mains</span>
          <span class="cat-word cat-grills">
            <span class="cat-line"></span>Grills
          </span>
          <span class="cat-word">Sides</span>
        </div>
      </div>
      <a href="/menu" class="btn-pill-outline-dark">See All Menu</a>
    </div>
    <div class="cat-right" use:reveal={{ delay: 120 }}>
      <div class="cat-oval">
        <img src="/photos/categories.jpg" alt="Caribbean food at Seaside Paradise" />
      </div>
      <p class="cat-desc">From oxtail and curry goat to jerk chicken and conch soup — every dish is slow-cooked, well-seasoned, and made the way it's supposed to be. Ask us what's hot today when you walk in.</p>
    </div>
  </div>
</section>

<!-- ── ABOUT ───────────────────────────────────────────────────── -->
<section class="about-section">
  <div class="about-inner" use:reveal={{ y: 16 }}>
    <h2 class="display about-title">
      <span>The Real</span>
      <span class="about-title-row"><span>Taste of</span><span>Grand Cayman</span></span>
    </h2>
    <p class="about-body">We cook fresh every day. Our menu follows the catch — whatever the fishermen bring in and local farms provide that morning is what ends up on your plate. No shortcuts. Just real Caribbean cooking.</p>
  </div>
</section>

<!-- ── ISLAND FAVOURITES ───────────────────────────────────────── -->
<section class="favourites-section">
  <div class="container">
    <p class="label lbl-red" use:reveal>CROWD FAVOURITES</p>
    <h2 class="display fav-title" use:reveal={{ delay: 60 }}>Island Favourites</h2>
    <div class="favourites-grid">
      {#each favourites as item, i}
        <div class="fav-card" class:fav-tall={i === 2} use:reveal={{ delay: i * 80 }}>
          <div class="fav-photo">
            <img src={item.img} alt="{item.name.join(' ')}" />
          </div>
          <div class="fav-footer">
            <div class="fav-name">{#each item.name as line}<p>{line}</p>{/each}</div>
            <span class="fav-price">{item.price}</span>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- ── OUR VALUES ─────────────────────────────────────────────── -->
<section class="values-section">
  <div class="values-inner">
  <p class="values-story-lbl" use:reveal>OUR STORY</p>
  <div class="values-card" use:reveal={{ delay: 100 }}>
    <div>
      <h2 class="display values-title">Our Values</h2>
      <p class="values-sub">Simple ingredients. Big flavors. Genuine warmth. That's what Seaside Paradise is built on.</p>
    </div>
    <ul class="values-list">
      {#each values as v, i}
        <li use:reveal={{ delay: 160 + i * 80 }}>
          <svg width="28" height="28" viewBox="0 0 28 28" fill="none" aria-hidden="true">
            <circle cx="14" cy="14" r="13" stroke="#2d1a14" stroke-width="1.5"/>
            <path d="M8.5 14l3.5 3.5 7.5-7" stroke="#2d1a14" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          <span>{v}</span>
        </li>
      {/each}
    </ul>
  </div>
  </div>
</section>

<!-- ── SPECIALS ───────────────────────────────────────────────── -->
<section class="specials-section">
  <div class="container">
    <p class="label lbl-red specials-lbl" use:reveal>TODAY'S SPECIALS</p>
    <h2 class="display specials-title" use:reveal={{ delay: 60 }}>Rondon &amp; Brown Stew Fish</h2>
    <div class="specials-layout">
      <div class="specials-col" use:reveal={{ delay: 80 }}>
        {#each specialsLeft as item, i}
          {#if i > 0}<hr class="s-hr" />{/if}
          <div class="s-item">
            <h3>{item.name}</h3>
            <p>{item.desc}</p>
          </div>
        {/each}
      </div>
      <div class="specials-photo" use:reveal={{ delay: 160, y: 16 }}>
        <img src="/photos/specials-circle.jpg" alt="Today's special" />
      </div>
      <div class="specials-col specials-col-r" use:reveal={{ delay: 80 }}>
        {#each specialsRight as item, i}
          {#if i > 0}<hr class="s-hr s-hr-r" />{/if}
          <div class="s-item s-item-r">
            <h3>{item.name}</h3>
            <p>{item.desc}</p>
          </div>
        {/each}
      </div>
    </div>
  </div>
</section>

<!-- ── CTA BANNER ─────────────────────────────────────────────── -->
<section class="cta-section">
  <div class="cta-inner">
    <h2 class="display cta-title" use:reveal={{ y: 20 }}>Good food, good vibes, every day.</h2>
    <div class="cta-buttons" use:reveal={{ delay: 120 }}>
      <a href="/contact" class="btn-pill-cream">Make A Reservation</a>
      <a href="/contact" class="btn-pill-outline-cream">Check Location</a>
    </div>
  </div>
</section>

<!-- ── FAQ ──────────────────────────────────────────────────────── -->
<section class="faq-section">
  <div class="container faq-inner">
    <div class="faq-left" use:reveal>
      <span class="label lbl-red">FAQ</span>
      <h2 class="display faq-title">Answers for<br />Questions</h2>
    </div>
    <div class="faq-right" use:reveal={{ delay: 100 }}>
      {#each faqs as faq, i}
        <div class="faq-item" class:faq-open={openFaq === i}>
          <button class="faq-q" on:click={() => toggleFaq(i)} aria-expanded={openFaq === i}>
            <span class="display faq-q-text">{faq.q}</span>
            <svg class="faq-icon" class:open={openFaq === i} width="32" height="32" viewBox="0 0 32 32" fill="none">
              <path d="M10 12l6 6 6-6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
          {#if openFaq === i}
            <p class="faq-a" transition:slide={{ duration: 280 }}>{faq.a}</p>
          {/if}
          <div class="faq-div" class:faq-div-thick={openFaq === i}></div>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- ── TESTIMONIALS ───────────────────────────────────────────── -->
<section class="testimonials-section">
  <div class="container">
    <p class="label lbl-amber" use:reveal>TESTIMONIALS</p>
    <h2 class="display testimonials-title" use:reveal={{ delay: 60 }}>What People Say</h2>
    <div class="testimonials-row" use:reveal={{ delay: 120 }}>
      <button class="arrow-btn" on:click={prevTestimonial} aria-label="Previous testimonial">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
          <path d="M15 18l-6-6 6-6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>
      {#key activeTestimonial}
        <div class="t-card" in:fade={{ duration: 320 }}>
          <div class="t-text">
            <div class="t-body">
              <p class="t-quote">{testimonials[activeTestimonial].quote}</p>
              <div class="t-author-block">
                <div class="t-line"></div>
                <p class="t-author">{testimonials[activeTestimonial].author}</p>
              </div>
            </div>
          </div>
          <div class="t-photo">
            <img src={testimonials[activeTestimonial].photo} alt="Restaurant" />
          </div>
        </div>
      {/key}
      <button class="arrow-btn" on:click={nextTestimonial} aria-label="Next testimonial">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
          <path d="M9 18l6-6-6-6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>
    </div>
  </div>
</section>

<!-- ── GALLERY ───────────────────────────────────────────────── -->
<section class="gallery-section">
  <div class="container">
    <div class="g-main" use:reveal={{ y: 16 }}>
      <img src="/photos/hero.jpg" alt="Seaside Paradise Restaurant" />
    </div>
    <div class="g-row" use:reveal={{ delay: 80 }}>
      <div class="g-thumb g-wide g-faded">
        <img src="/photos/about-hero.jpg" alt="" />
      </div>
      <div class="g-thumb"><img src="/photos/testimonials-photo.jpg" alt="" /></div>
      <div class="g-thumb"><img src="/photos/categories.jpg" alt="" /></div>
      <div class="g-thumb"><img src="/photos/values-bg.jpg" alt="" /></div>
      <div class="g-thumb"><img src="/photos/services-interior.jpg" alt="" /></div>
    </div>
  </div>
</section>

<style>
/* ── Label colour overrides ───────────────────────────────────── */
.lbl-red   { color: var(--red);   font-size: 16px; letter-spacing: 0.13em; }
.lbl-amber { color: var(--amber); font-size: 16px; letter-spacing: 0.13em; }

/* ── Pill buttons ─────────────────────────────────────────────── */
.btn-pill-cream {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 13px 56px;
  border-radius: 100px;
  background: var(--cream);
  color: var(--dark);
  font-family: var(--font-label);
  font-weight: 600;
  font-size: clamp(17px, 1.8vw, 26px);
  line-height: 1.25;
  white-space: nowrap;
  transition: opacity 0.2s, transform 0.2s, box-shadow 0.2s;
  box-shadow: 0 4px 20px rgba(247,240,220,0.15);
}
.btn-pill-cream:hover {
  opacity: 0.92;
  transform: translateY(-2px);
  box-shadow: 0 8px 32px rgba(247,240,220,0.25);
}

.btn-pill-outline-dark {
  display: inline-flex;
  align-items: center;
  padding: 9px 32px;
  border: 1.5px solid var(--dark);
  border-radius: 100px;
  color: var(--dark);
  font-family: var(--font-body);
  font-size: 16px;
  transition: background 0.25s, color 0.25s, border-color 0.25s, transform 0.2s;
}
.btn-pill-outline-dark:hover {
  background: var(--dark);
  color: var(--cream);
  transform: translateY(-1px);
}

.btn-pill-outline-cream {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 9px 32px;
  border: 1.5px solid var(--cream);
  border-radius: 100px;
  color: var(--cream);
  font-family: var(--font-body);
  font-size: 16px;
  transition: background 0.25s, transform 0.2s;
}
.btn-pill-outline-cream:hover {
  background: rgba(247,240,220,0.12);
  transform: translateY(-1px);
}

/* ── HERO ─────────────────────────────────────────────────────── */
.hero {
  position: relative;
  margin-top: calc(-1 * var(--navbar-h));
  min-height: 100svh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: url('/photos/hero.jpg') center / cover no-repeat #3D5A50;
  overflow: hidden;
}
.hero::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to top,
    rgba(26,9,5,0.78) 0%,
    rgba(26,9,5,0.38) 45%,
    rgba(26,9,5,0.12) 100%
  );
}
.hero-content {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 28px;
  text-align: center;
  padding: 60px 20px;
  animation: heroFadeUp 1s cubic-bezier(.4,0,.2,1) both;
}
@keyframes heroFadeUp {
  from { opacity: 0; transform: translateY(32px); }
  to   { opacity: 1; transform: translateY(0); }
}
.hero-title {
  font-size: clamp(48px, 9.5vw, 136px);
  color: var(--cream);
  line-height: 1.0;
  text-shadow: 0 2px 40px rgba(26,9,5,0.4);
}
.hero-sub {
  font-size: clamp(16px, 1.4vw, 20px);
  color: rgba(247,240,220,0.72);
  line-height: 1.6;
  max-width: 640px;
}

/* Scroll indicator */
.scroll-hint {
  position: absolute;
  bottom: 32px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 1;
  animation: heroFadeUp 1.2s .6s cubic-bezier(.4,0,.2,1) both;
}
.scroll-hint span {
  display: block;
  width: 1.5px;
  height: 44px;
  background: linear-gradient(to bottom, transparent, rgba(247,240,220,0.5));
  margin: 0 auto;
  animation: scrollPulse 2s ease-in-out infinite;
}
@keyframes scrollPulse {
  0%, 100% { opacity: 0.4; transform: scaleY(1); }
  50%       { opacity: 1;   transform: scaleY(1.12); }
}

/* ── CATEGORIES ───────────────────────────────────────────────── */
.categories-section {
  background: #fffff4;
  padding: var(--section-pad) clamp(20px, 5.6vw, 80px);
}
.categories-inner {
  max-width: var(--container);
  margin: 0 auto;
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 60px;
}
.cat-left {
  flex-shrink: 0;
  display: flex;
  flex-direction: column;
  gap: clamp(60px, 8vw, 120px);
}
.cat-list {
  display: flex;
  flex-direction: column;
  gap: clamp(12px, 2vw, 30px);
  margin-top: 16px;
}
.cat-word {
  font-family: var(--font-display);
  font-size: clamp(36px, 4.4vw, 64px);
  color: var(--dark);
  line-height: 1.1;
  transition: color 0.22s, transform 0.22s;
  cursor: default;
}
.cat-word:hover { color: var(--red); transform: translateX(6px); }
.cat-grills { display: flex; align-items: center; gap: 24px; }
.cat-grills:hover { transform: translateX(0); } /* override, line doesn't shift */
.cat-grills:hover > span:last-child { color: var(--red); }
.cat-line {
  display: block;
  width: 88px;
  height: 1px;
  background: var(--dark);
  flex-shrink: 0;
  transition: width 0.3s, background 0.22s;
}
.cat-grills:hover .cat-line { width: 104px; background: var(--red); }
.cat-right {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  gap: 32px;
  align-self: stretch;
}
.cat-oval {
  width: 100%;
  height: clamp(240px, 29vw, 418px);
  border-radius: 500px;
  overflow: hidden;
  flex-shrink: 0;
  box-shadow: 0 20px 60px rgba(26,9,5,0.14);
}
.cat-oval img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.7s cubic-bezier(.4,0,.2,1);
}
.cat-oval:hover img { transform: scale(1.04); }
.cat-desc {
  font-size: clamp(16px, 1.4vw, 20px);
  color: rgba(45,26,20,0.68);
  line-height: 1.6;
  text-align: center;
}

/* ── ABOUT ────────────────────────────────────────────────────── */
.about-section {
  padding: 0 clamp(20px, 5.6vw, 80px);
  background: #fffff4;
}
.about-inner {
  position: relative;
  max-width: var(--container);
  margin: 0 auto;
  height: clamp(360px, 44vw, 640px);
  background: url('/photos/testimonials-photo.jpg') center / cover no-repeat #3D5A50;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  padding: clamp(28px, 3.3vw, 48px) clamp(24px, 3vw, 40px) clamp(28px, 3.3vw, 40px) clamp(32px, 3.3vw, 48px);
  overflow: hidden;
  border-radius: 3px;
}
.about-inner::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(
    105deg,
    rgba(26,9,5,0.72) 0%,
    rgba(26,9,5,0.45) 45%,
    rgba(26,9,5,0.28) 100%
  );
}
.about-title {
  position: relative;
  font-size: clamp(36px, 5.5vw, 80px);
  color: var(--cream);
  line-height: 1.08;
  flex-shrink: 0;
  display: flex;
  flex-direction: column;
}
.about-title-row {
  display: flex;
  gap: 0.25em;
  align-items: baseline;
}
.about-body {
  position: relative;
  font-size: clamp(15px, 1.4vw, 20px);
  color: rgba(247,240,220,0.72);
  line-height: 1.62;
  max-width: 560px;
  padding-bottom: 8px;
  align-self: flex-end;
}

/* ── FAVOURITES ───────────────────────────────────────────────── */
.favourites-section {
  background: #fffff4;
  padding: var(--section-pad) clamp(20px, 5.6vw, 80px);
}
.fav-title {
  font-size: clamp(40px, 5.5vw, 80px);
  color: var(--dark);
  margin: 8px 0 64px;
}
.favourites-grid {
  display: flex;
  align-items: flex-end;
  gap: clamp(16px, 1.7vw, 24px);
}
.fav-card {
  flex: 1;
  min-width: 0;
  display: flex;
  flex-direction: column;
  gap: 20px;
  height: 400px;
  transition: transform 0.3s cubic-bezier(.4,0,.2,1);
}
.fav-tall { height: 480px; }
.fav-card:hover { transform: translateY(-5px); }
.fav-photo {
  flex: 1;
  min-height: 0;
  overflow: hidden;
  position: relative;
}
.fav-photo::after {
  content: '';
  position: absolute;
  inset: 0;
  background: rgba(26,9,5,0);
  transition: background 0.4s;
}
.fav-card:hover .fav-photo::after { background: rgba(26,9,5,0.08); }
.fav-photo img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.7s cubic-bezier(.4,0,.2,1);
}
.fav-card:hover .fav-photo img { transform: scale(1.05); }
.fav-footer {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  flex-shrink: 0;
  gap: 8px;
}
.fav-name {
  font-family: var(--font-label);
  font-weight: 600;
  font-size: clamp(17px, 1.8vw, 26px);
  line-height: 1.25;
  color: var(--dark);
}
.fav-price {
  font-size: 20px;
  color: rgba(45,26,20,0.38);
  flex-shrink: 0;
}

/* ── VALUES ───────────────────────────────────────────────────── */
.values-section {
  position: relative;
  padding: clamp(60px, 8vw, 120px) clamp(20px, 5.6vw, 80px);
  overflow: hidden;
  background: url('/photos/values-bg.jpg') center / cover no-repeat #3D5A50;
  min-height: 480px;
}
.values-section::before {
  content: '';
  position: absolute;
  inset: 0;
  background: rgba(26,9,5,0.38);
}
.values-inner {
  position: relative;
  z-index: 1;
  max-width: var(--container);
  margin: 0 auto;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 40px;
}
.values-story-lbl {
  font-family: var(--font-label);
  font-weight: 600;
  font-size: 16px;
  letter-spacing: 0.13em;
  text-transform: uppercase;
  color: var(--cream);
  opacity: 0.75;
}
.values-card {
  background: var(--cream);
  padding: clamp(32px, 3vw, 48px) clamp(24px, 3vw, 48px) clamp(40px, 4vw, 60px);
  display: flex;
  flex-direction: column;
  gap: 32px;
  max-width: min(585px, 55vw);
  flex-shrink: 0;
  box-shadow: 0 24px 80px rgba(26,9,5,0.28);
}
.values-title {
  font-size: clamp(36px, 4.4vw, 64px);
  color: var(--dark);
  line-height: 1.1;
}
.values-sub {
  font-size: clamp(16px, 1.4vw, 20px);
  color: rgba(45,26,20,0.68);
  line-height: 1.6;
  margin-top: 8px;
  max-width: 460px;
}
.values-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 14px;
  padding-left: 8px;
}
.values-list li {
  display: flex;
  align-items: center;
  gap: 14px;
  font-weight: 600;
  font-size: 16px;
  color: var(--dark);
  line-height: 1.5;
}
.values-list svg { flex-shrink: 0; }

/* ── SPECIALS ─────────────────────────────────────────────────── */
.specials-section {
  background: #fffff4;
  padding: var(--section-pad) clamp(20px, 5.6vw, 80px);
}
.specials-lbl { display: block; letter-spacing: 0.3em; }
.specials-title {
  font-size: clamp(36px, 4.4vw, 64px);
  color: var(--dark);
  margin: 8px 0 clamp(40px, 4vw, 64px);
}
.specials-layout {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: clamp(16px, 2.8vw, 40px);
  padding: 0 clamp(0px, 1.4vw, 20px);
}
.specials-col {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: clamp(32px, 5.7vw, 82px);
}
.specials-col-r { align-items: flex-end; text-align: right; }
.s-item { display: flex; flex-direction: column; gap: 8px; }
.s-item-r { align-items: flex-end; }
.s-item h3 {
  font-family: var(--font-body);
  font-weight: 600;
  font-size: 20px;
  color: var(--dark);
  line-height: 1.5;
  white-space: nowrap;
  transition: color 0.2s;
}
.s-item:hover h3 { color: var(--red); }
.s-item p {
  font-size: 16px;
  color: rgba(45,26,20,0.68);
  line-height: 1.6;
  max-width: 320px;
}
.s-item-r p { margin-left: auto; }
.s-hr {
  border: none;
  border-top: 1px solid rgba(45,26,20,0.22);
  width: 72px;
  margin: 0;
}
.s-hr-r { margin-left: auto; }
.specials-photo {
  flex-shrink: 0;
  width: clamp(240px, 35.6vw, 512px);
  height: clamp(240px, 35.6vw, 512px);
  border-radius: 50%;
  overflow: hidden;
  box-shadow: 0 24px 72px rgba(26,9,5,0.16);
}
.specials-photo img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.8s cubic-bezier(.4,0,.2,1);
}
.specials-photo:hover img { transform: scale(1.04); }

/* ── CTA ──────────────────────────────────────────────────────── */
.cta-section {
  padding: 0 clamp(20px, 5.6vw, 80px);
  background: #fffff4;
}
.cta-inner {
  position: relative;
  max-width: var(--container);
  margin: 0 auto;
  background: url('/photos/cta-bg.jpg') center / cover no-repeat #3D5A50;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 32px;
  padding: clamp(60px, 8vw, 120px) 40px;
}
.cta-inner::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, rgba(26,9,5,0.38) 0%, rgba(26,9,5,0.54) 100%);
}
.cta-title {
  position: relative;
  z-index: 1;
  font-size: clamp(40px, 5.5vw, 80px);
  color: var(--cream);
  line-height: 1.08;
  text-align: center;
}
.cta-buttons {
  position: relative;
  z-index: 1;
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  justify-content: center;
}

/* ── FAQ ──────────────────────────────────────────────────────── */
.faq-section {
  background: #fffff4;
  padding: var(--section-pad) clamp(20px, 5.6vw, 80px);
}
.faq-inner {
  display: grid;
  grid-template-columns: 1fr 1.8fr;
  gap: clamp(40px, 5.6vw, 80px);
  align-items: start;
}
.faq-left { position: sticky; top: calc(var(--navbar-h) + 24px); }
.faq-title {
  font-size: clamp(40px, 5.5vw, 80px);
  color: var(--dark);
  margin-top: 8px;
  line-height: 1.08;
}
.faq-right { display: flex; flex-direction: column; }
.faq-item { }
.faq-open .faq-q-text { color: var(--dark); }
.faq-q {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  padding: 22px 0;
  text-align: left;
  color: var(--dark);
  transition: color 0.2s;
}
.faq-q:hover { color: var(--red); }
.faq-open .faq-q { color: var(--dark); }
.faq-q-text {
  font-family: var(--font-display);
  font-size: clamp(20px, 2.5vw, 36px);
  line-height: 1.2;
}
.faq-icon {
  flex-shrink: 0;
  transition: transform 0.32s cubic-bezier(.4,0,.2,1);
  color: var(--dark);
}
.faq-icon.open { transform: rotate(180deg); }
.faq-a {
  padding-bottom: 22px;
  font-size: clamp(16px, 1.4vw, 20px);
  color: rgba(45,26,20,0.68);
  line-height: 1.62;
}
.faq-div { height: 1px; background: rgba(45,26,20,0.14); }
.faq-div-thick { height: 2px; background: var(--dark); }

/* ── TESTIMONIALS ─────────────────────────────────────────────── */
.testimonials-section {
  background: var(--bg-dark);
  padding: clamp(60px, 7vw, 100px) clamp(20px, 5.6vw, 80px) clamp(60px, 8vw, 120px);
}
.testimonials-section .label { display: block; }
.testimonials-title {
  font-size: clamp(36px, 4.4vw, 64px);
  color: var(--cream);
  margin: 8px 0 56px;
}
.testimonials-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: clamp(16px, 2vw, 32px);
}
.arrow-btn {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  border: 1.5px solid rgba(247,240,220,0.28);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  color: rgba(247,240,220,0.7);
  transition: border-color 0.22s, background 0.22s, color 0.22s, transform 0.2s;
}
.arrow-btn:hover {
  border-color: var(--cream);
  background: rgba(247,240,220,0.09);
  color: var(--cream);
  transform: scale(1.06);
}
.t-card {
  flex: 1;
  display: flex;
  height: 402px;
  min-width: 0;
  max-width: 1064px;
  overflow: hidden;
  box-shadow: 0 24px 72px rgba(0,0,0,0.35);
}
.t-text {
  background: var(--cream);
  flex: 0 0 66%;
  padding: clamp(32px, 4vw, 64px) clamp(24px, 3.9vw, 56px);
  display: flex;
}
.t-body {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 100%;
}
.t-quote {
  font-size: clamp(16px, 1.4vw, 20px);
  color: rgba(45,26,20,0.68);
  line-height: 1.62;
}
.t-author-block { display: flex; flex-direction: column; gap: 24px; }
.t-line { width: 32px; height: 2px; background: var(--dark); }
.t-author {
  font-weight: 600;
  font-size: clamp(16px, 1.4vw, 20px);
  color: var(--dark);
  line-height: 1.5;
}
.t-photo { flex: 1; overflow: hidden; }
.t-photo img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.8s cubic-bezier(.4,0,.2,1);
}
.t-card:hover .t-photo img { transform: scale(1.04); }

/* ── GALLERY ──────────────────────────────────────────────────── */
.gallery-section {
  background: #fffff4;
  padding: var(--section-pad) clamp(20px, 5.6vw, 80px);
}
.g-main {
  height: clamp(280px, 41.7vw, 600px);
  overflow: hidden;
  margin-bottom: 20px;
  position: relative;
}
.g-main img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.8s cubic-bezier(.4,0,.2,1);
}
.g-main:hover img { transform: scale(1.025); }
.g-row {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1fr 1fr;
  gap: 20px;
  height: 200px;
}
.g-thumb {
  overflow: hidden;
  position: relative;
}
.g-thumb::after {
  content: '';
  position: absolute;
  inset: 0;
  background: rgba(26,9,5,0);
  transition: background 0.35s;
}
.g-thumb:hover::after { background: rgba(26,9,5,0.12); }
.g-thumb img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.6s cubic-bezier(.4,0,.2,1);
}
.g-thumb:hover img { transform: scale(1.07); }
.g-faded { opacity: 0.5; transition: opacity 0.3s; }
.g-faded:hover { opacity: 0.75; }

/* ── RESPONSIVE ───────────────────────────────────────────────── */
@media (max-width: 1024px) {
  .favourites-grid { flex-wrap: wrap; }
  .fav-card, .fav-tall { flex: 0 0 calc(50% - 12px); height: 360px; }
  .specials-photo { width: 280px; height: 280px; }
  .g-row { grid-template-columns: 1fr 1fr 1fr; height: auto; }
  .g-wide { grid-column: 1 / -1; }
  .g-thumb { height: 180px; }
}

@media (max-width: 900px) {
  .faq-left { position: static; }
  .faq-inner { grid-template-columns: 1fr; gap: 40px; }
  .t-card { height: auto; flex-direction: column; }
  .t-text { flex: none; }
  .t-photo { height: 260px; flex: none; }
}

@media (max-width: 768px) {
  .categories-inner { flex-direction: column; }
  .cat-right { align-self: auto; }
  .cat-oval { height: 260px; border-radius: 24px; }

  .about-inner { flex-direction: column; align-items: flex-start; height: auto; min-height: 380px; }
  .about-body { padding-bottom: 0; max-width: 100%; }

  .fav-card, .fav-tall { flex: 0 0 calc(50% - 8px); height: 320px; }

  .values-section { flex-direction: column; align-items: flex-start; gap: 40px; }
  .values-card { max-width: 100%; }

  .specials-layout { flex-direction: column; align-items: center; }
  .specials-col, .specials-col-r { align-items: flex-start; text-align: left; width: 100%; }
  .s-item-r { align-items: flex-start; }
  .s-item-r p, .s-hr-r { margin-left: 0; }
  .specials-photo { width: 260px; height: 260px; }

  .testimonials-row { gap: 12px; }
  .arrow-btn { width: 48px; height: 48px; }

  .g-row { grid-template-columns: 1fr 1fr; height: auto; }
  .g-thumb { height: 160px; }
  .g-wide { grid-column: 1 / -1; height: 200px; }
}

@media (max-width: 900px) {
  .hero {
    margin-top: calc(-1 * var(--navbar-h-mobile));
    min-height: calc(100svh + var(--navbar-h-mobile));
  }
}

@media (max-width: 480px) {
  .hero-title { font-size: 40px; }
  .scroll-hint { display: none; }
  .fav-card, .fav-tall { flex: 0 0 100%; height: 300px; }
  .cta-buttons { flex-direction: column; align-items: center; width: 100%; }
  .cta-buttons a { width: 100%; max-width: 320px; justify-content: center; }
  .testimonials-row { flex-wrap: wrap; justify-content: center; }
  .t-card { width: 100%; }
  .g-row { grid-template-columns: 1fr; height: auto; }
  .g-thumb { height: 200px; }
  .g-wide { grid-column: auto; height: 200px; }
}
</style>
