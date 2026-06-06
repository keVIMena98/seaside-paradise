<script>
  const days = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];

  const menuData = {
    Monday: [
      { name: 'Chicken Soup',  price: '$7',  desc: 'Homemade chicken soup simmered with local vegetables, dumplings and island spices. A warm, comforting bowl to start your meal.',                          photo: '/photos/menu-soup.jpg' },
      { name: 'Fry Chicken',   price: '$9',  desc: 'Golden-fried chicken seasoned Caymanian-style. Crispy on the outside, juicy all the way through. Served with your choice of side.',                     photo: '/photos/menu-fry-chicken.jpg' },
      { name: 'Curry Chicken', price: '$10', desc: 'Tender chicken slow-cooked in a rich Caribbean curry sauce with potatoes and peppers. Served with white rice or rice and peas.',                         photo: '/photos/menu-curry.jpg' },
    ],
    Tuesday: [
      { name: 'Oxtail',        price: '$12', desc: 'Fall-off-the-bone oxtail braised for hours in a rich, dark gravy. Served with rice and peas and fresh coleslaw on the side.',                           photo: '/photos/menu-oxtail.jpg', featured: true },
      { name: 'BBQ Chicken',   price: '$10', desc: 'Smoky, charred chicken glazed with our homemade BBQ sauce. Bold, sticky and full of island flavor every single time.',                                   photo: '/photos/menu-bbq.jpg' },
      { name: 'Jerk Chicken',  price: '$10', desc: 'Marinated overnight in scotch bonnet, allspice and fresh thyme. Grilled until the skin blisters and the inside stays juicy.',                           photo: '/photos/menu-jerk.jpg' },
    ],
    Wednesday: [
      { name: 'Brown Stew Fish', price: '$12', desc: 'Fresh local fish braised low and slow in a rich brown gravy with peppers, onions and island spices.',                                                  photo: '/photos/menu-fish.jpg' },
      { name: 'Stew Beef',       price: '$11', desc: 'Braised beef in rich brown gravy with fresh vegetables and island spices. Served with rice and peas.',                                                 photo: '/photos/menu-stew-beef.jpg' },
      { name: 'Pepper Steak',    price: '$12', desc: 'Tender beef with mixed peppers and our house pepper sauce. Bold and deeply flavourful.',                                                               photo: '/photos/menu-pepper-steak.jpg' },
    ],
    Thursday: [
      { name: 'Stew Conch',    price: '$12', desc: 'Tender conch stew braised in tomato and island spices. A true Caribbean classic.',                                                                       photo: '/photos/menu-conch.jpg' },
      { name: 'Rondon',        price: '$11', desc: 'The Caymanian one-pot — salt fish in coconut milk with breadfruit, dumplings and ground provisions.',                                                    photo: '/photos/menu-rondon.jpg', featured: true },
      { name: 'Roast Pork',    price: '$11', desc: 'Slow-oven-roasted pork seasoned with Caymanian herbs and spices. Tender, moist and deeply flavorful.',                                                  photo: '/photos/menu-pork.jpg' },
    ],
    Friday: [
      { name: 'Jerk Pork',     price: '$12', desc: 'Pork marinated in jerk spices, grilled over open fire. Smoky, spicy and utterly satisfying.',                                                           photo: '/photos/menu-jerk-pork.jpg' },
      { name: 'Jerk Chicken',  price: '$10', desc: 'Our most popular grill item — marinated overnight and packed with flavour. Full of island character.',                                                   photo: '/photos/menu-jerk.jpg' },
      { name: 'Conch & Beans', price: '$12', desc: 'A Caymanian staple — slow cooked with butter beans. Hearty and homestyle.',                                                                             photo: '/photos/menu-conch.jpg' },
    ],
    Saturday: [
      { name: 'Roast Beef',    price: '$12', desc: 'Slow-roasted beef seasoned with Caribbean spices. Carved fresh and served with gravy and your choice of side.',                                          photo: '/photos/menu-roast-beef.jpg' },
      { name: 'Stew Chicken',  price: '$10', desc: 'Chicken pieces slow-stewed in a savory brown sauce with onions, thyme and local seasonings. A classic Caribbean comfort dish.',                         photo: '/photos/menu-stew-chicken.jpg' },
      { name: 'Jerk Chicken',  price: '$10', desc: 'Marinated overnight in scotch bonnet, allspice and fresh thyme. Grilled until the skin blisters and the inside stays juicy.',                           photo: '/photos/menu-jerk.jpg' },
    ],
  };

  let activeDay = 'Monday';
</script>

<svelte:head>
  <title>Our Daily Rotating Menu — Seaside Paradise</title>
</svelte:head>

<!-- ── HEADING ── -->
<section class="menu-heading">
  <div class="heading-inner">
    <h1 class="menu-title">Our Daily<br />Rotating Menu</h1>
  </div>
</section>

<!-- ── DAY TABS ── -->
<section class="menu-section">
  <div class="menu-inner">
    <div class="day-tabs" role="tablist" aria-label="Menu days">
      {#each days as day}
        <button
          class="day-tab"
          class:active={activeDay === day}
          on:click={() => activeDay = day}
          role="tab"
          aria-selected={activeDay === day}
        >
          {day.toUpperCase()}
        </button>
      {/each}
    </div>

    <!-- Menu cards -->
    <div class="menu-grid" role="tabpanel">
      {#each menuData[activeDay] as item (item.name)}
        <div class="menu-card" class:featured={item.featured}>
          <div class="card-photo photo-bg" style="background-image:url('{item.photo}')"></div>
          <div class="card-content">
            <div class="card-text-wrap">
              <div class="card-meta">
                <span class="card-price">{item.price}</span>
                <h3 class="card-name">{item.name}</h3>
              </div>
              <p class="card-desc">{item.desc}</p>
            </div>
            <div class="card-line"></div>
          </div>
        </div>
      {/each}
    </div>

    <p class="menu-note">Menu changes daily based on what's fresh. Items may vary — ask us what's hot today.</p>
  </div>
</section>

<!-- ── CTA ── -->
<section class="cta-section">
  <div class="cta-pill photo-bg" style="background-image:url('/photos/cta-bg.jpg')">
    <div class="cta-overlay"></div>
    <div class="cta-text">
      <span class="cta-line cream">Good food,</span>
      <span class="cta-line amber">good vibes,</span>
      <span class="cta-line cream">every day.</span>
    </div>
    <a href="/contact" class="cta-btn">Come Visit Us</a>
  </div>
</section>

<style>
/* ── HEADING ── */
.menu-heading {
  background: #fffff4;
  padding: clamp(56px, 7vw, 100px) clamp(24px, 5.6vw, 80px) clamp(40px, 5vw, 72px);
  text-align: center;
}
.heading-inner { max-width: 1280px; margin: 0 auto; }
.menu-title {
  font-family: var(--font-display);
  font-size: clamp(48px, 7vw, 80px);
  line-height: 1.1;
  color: var(--dark);
  text-align: center;
}

/* ── MENU SECTION ── */
.menu-section { background: #fffff4; padding: 0 clamp(24px, 5.6vw, 80px) var(--section-pad); }
.menu-inner { max-width: 1280px; margin: 0 auto; }

/* Day tabs */
.day-tabs {
  display: flex;
  gap: clamp(24px, 5vw, 72px);
  margin-bottom: 64px;
  overflow-x: auto;
  scrollbar-width: none;
}
.day-tabs::-webkit-scrollbar { display: none; }

.day-tab {
  font-family: var(--font-body);
  font-weight: 600;
  font-size: 16px;
  line-height: 24px;
  letter-spacing: 1.92px;
  color: var(--dark);
  opacity: 0.5;
  padding-bottom: 12px;
  border-bottom: 2px solid transparent;
  white-space: nowrap;
  transition: opacity 0.2s, border-color 0.2s;
  background: none;
  border-top: none;
  border-left: none;
  border-right: none;
  cursor: pointer;
}
.day-tab:hover { opacity: 0.75; }
.day-tab.active {
  opacity: 1;
  border-bottom-color: var(--dark);
}

/* Menu grid */
.menu-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0;
  margin-bottom: 40px;
}

.menu-card {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.card-photo {
  height: 320px;
  width: 100%;
  background-color: #5A7060;
  background-size: cover;
  background-position: center;
}

.card-content {
  width: 100%;
  background: var(--cream);
  border: 1px solid rgba(45,26,20,0.2);
  border-top: none;
  display: flex;
  flex-direction: column;
  gap: 40px;
  align-items: center;
  padding: 24px 20px 32px;
}

.card-text-wrap {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 100%;
}

.card-meta {
  display: flex;
  flex-direction: column;
  gap: 8px;
  align-items: center;
  width: 100%;
}

.card-price {
  font-family: var(--font-body);
  font-size: 20px;
  line-height: 30px;
  color: var(--dark);
  opacity: 0.4;
  text-align: right;
  width: 100%;
}

.card-name {
  font-family: var(--font-label);
  font-weight: 600;
  font-size: 26px;
  line-height: 32px;
  color: var(--dark);
  text-align: center;
  width: 100%;
}

.card-desc {
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 24px;
  color: var(--dark);
  opacity: 0.7;
  text-align: center;
}

.card-line {
  width: 80px;
  height: 1px;
  background: var(--dark);
}

/* Featured (dark) card variant */
.menu-card.featured .card-content {
  background: var(--bg-dark);
  border-color: transparent;
}
.menu-card.featured .card-name { color: var(--amber); }
.menu-card.featured .card-price { color: var(--cream); opacity: 0.7; }
.menu-card.featured .card-desc { color: var(--cream); opacity: 0.9; }
.menu-card.featured .card-line { background: var(--amber); }

.menu-note {
  font-size: 14px;
  color: var(--text-muted);
  font-style: italic;
  text-align: center;
}

/* ── CTA ── */
.cta-section {
  background: #fffff4;
  padding: 0 clamp(24px, 5.6vw, 80px) var(--section-pad);
}
.cta-pill {
  position: relative;
  max-width: 1280px;
  margin: 0 auto;
  border-radius: 1000px;
  overflow: hidden;
  padding: 80px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 36px;
  background-color: #3D5A50;
  background-size: cover;
  background-position: center;
}
.cta-overlay {
  position: absolute;
  inset: 0;
  background: rgba(26,9,5,0.6);
}
.cta-text {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: var(--font-display);
  font-size: clamp(40px, 6vw, 80px);
  line-height: 1.1;
  text-align: center;
}
.cta-line { display: block; }
.cta-line.cream { color: var(--cream); }
.cta-line.amber { color: var(--amber); }

.cta-btn {
  position: relative;
  z-index: 1;
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
  text-decoration: none;
  white-space: nowrap;
  transition: opacity 0.2s;
}
.cta-btn:hover { opacity: 0.9; }

/* ── RESPONSIVE ── */
@media (max-width: 1024px) {
  .menu-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 680px) {
  .menu-grid { grid-template-columns: 1fr; }
  .cta-pill { border-radius: 40px; padding: 56px 32px; }
  .day-tabs { gap: 20px; }
}
@media (max-width: 480px) {
  .card-photo { height: 220px; }
  .cta-section { padding-left: 0; padding-right: 0; }
  .cta-pill { border-radius: 0; }
}
</style>
