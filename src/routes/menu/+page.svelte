<script>
  const days = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'];
  let activeDay = 'Monday';

  const dailyMenu = [
    {
      category: 'Chicken',
      items: [
        { name: 'Fry Chicken',       price: '$6–10' },
        { name: 'Baked Chicken',     price: '$7–12' },
        { name: 'Curry Chicken' },
        { name: 'BBQ Chicken',       price: '$9–12' },
        { name: 'Jerk Chicken',      price: '$9–12' },
        { name: 'Homestyle Chicken' },
        { name: 'Barbie Fry' },
      ],
    },
    {
      category: 'Meat & Stews',
      items: [
        { name: 'Oxtail',              price: '$10–15' },
        { name: 'Stew Beef',           price: '$10–14' },
        { name: 'Curry Goat',          price: '$10–14' },
        { name: 'Jerk Pork',           price: '$9–12' },
        { name: 'Roast Pork' },
        { name: 'Roast Beef' },
        { name: 'Pot Roast Pork' },
        { name: 'Pepper Steak' },
        { name: 'Stew Pork' },
        { name: 'Spaghetti & Meatballs' },
        { name: 'Cowfoot & Beans' },
      ],
    },
    {
      category: 'Soups',
      items: [
        { name: 'Chicken Soup' },
        { name: 'Beef Soup' },
        { name: 'Cow Foot Soup', price: '$5–10' },
        { name: 'Conch Soup' },
      ],
    },
    {
      category: 'Seafood',
      items: [
        { name: 'Brown Stew Fish' },
        { name: 'Fry Fish' },
        { name: 'Stew Conch' },
      ],
    },
  ];

  const fishItems = [
    { name: 'Fry Fish',          price: '$16–30' },
    { name: 'Steam Fish',        price: '$16–30' },
    { name: 'Brown Stew Fish',   price: '$16–30' },
    { name: 'Escovitch Fish' },
  ];

  const shrimpItems = [
    { name: 'Pepper Shrimp',   price: '$15' },
    { name: 'Garlic Shrimp',   price: '$15' },
    { name: 'Curry Shrimp',    price: '$15' },
    { name: 'Coconut Shrimp',  price: '$15' },
    { name: 'Fry Shrimp' },
  ];

  const grillsItems = [
    { name: 'Chicken Tenders with Chips' },
    { name: 'Chicken Stir Fry' },
    { name: 'Escovitch Chicken with Press Plantin' },
    { name: 'Hot Dog' },
    { name: 'Hamburgers — Beef or Chicken',  price: '$10' },
    { name: 'Chicken and Chips' },
    { name: 'Fish Sticks and Fries' },
    { name: 'Wings and Fries',               price: '$12' },
    { name: 'Chicken Burger' },
    { name: 'Fish Burger' },
    { name: 'BBQ Wings',                     price: '$12' },
  ];

  const sides = [
    { name: 'White Rice',      free: true },
    { name: 'Rice & Beans',    free: true },
    { name: 'Pasta',           free: true },
    { name: 'Coleslaw',        free: true },
    { name: 'Raw Vegetable',   free: true },
    { name: 'Festival (x3)',   price: '$2' },
    { name: 'Steam Bami',      price: '$5' },
    { name: 'Steam Veg',       price: '$5' },
    { name: 'Stir Fry Veg',    price: '$5' },
  ];

  const drinks = [
    { name: 'Pine & Ginger',             price: '$6' },
    { name: 'Strawberry Mango',          price: '$6' },
    { name: 'Soursop with Lime',         price: '$6' },
    { name: 'Peanut Punch (Strong Back)', price: '$7' },
  ];
</script>

<svelte:head>
  <title>Our Daily Menu — Seaside Paradise</title>
</svelte:head>

<!-- ── HEADING ── -->
<section class="menu-heading">
  <div class="heading-inner">
    <h1 class="menu-title">Our Daily<br />Menu</h1>
    <p class="menu-hours">Open every day · 11:00 AM – 10:30 PM</p>
  </div>
</section>

<!-- ── DAY TABS ── -->
<section class="tabs-section">
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
          {day.slice(0, 3).toUpperCase()}
        </button>
      {/each}
    </div>
  </div>
</section>

<!-- ── DAILY MENU ── -->
<section class="daily-section">
  <div class="menu-inner">
    <div class="menu-grid">
      {#each dailyMenu as section}
        <div class="menu-cat">
          <h3 class="cat-label">{section.category}</h3>
          {#each section.items as item}
            <div class="menu-row">
              <span class="item-name">{item.name}</span>
              {#if item.price}<span class="item-price">{item.price}</span>{/if}
            </div>
          {/each}
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- ── DONE TO ORDER ── -->
<section class="dto-section">
  <div class="menu-inner">
    <div class="dto-head">
      <p class="eyebrow-amber">PREPARED FRESH</p>
      <h2 class="dto-title">Done to Order</h2>
    </div>

    <div class="dto-pair">
      <div class="menu-cat">
        <h3 class="cat-label cat-amber">Fish</h3>
        {#each fishItems as item}
          <div class="menu-row row-dark">
            <span class="item-name name-cream">{item.name}</span>
            {#if item.price}<span class="item-price price-cream">{item.price}</span>{/if}
          </div>
        {/each}
      </div>
      <div class="menu-cat">
        <h3 class="cat-label cat-amber">Shrimp</h3>
        {#each shrimpItems as item}
          <div class="menu-row row-dark">
            <span class="item-name name-cream">{item.name}</span>
            {#if item.price}<span class="item-price price-cream">{item.price}</span>{/if}
          </div>
        {/each}
      </div>
    </div>

    <div class="menu-cat">
      <h3 class="cat-label cat-amber">Grills &amp; Mains</h3>
      <div class="grills-grid">
        {#each grillsItems as item}
          <div class="menu-row row-dark">
            <span class="item-name name-cream">{item.name}</span>
            {#if item.price}<span class="item-price price-cream">{item.price}</span>{/if}
          </div>
        {/each}
      </div>
    </div>
  </div>
</section>

<!-- ── SIDES & DRINKS ── -->
<section class="extras-section">
  <div class="menu-inner extras-row">

    <div class="extras-col">
      <p class="eyebrow-red">WITH YOUR MEAL</p>
      <h2 class="extras-title">Sides</h2>
      {#each sides as item}
        <div class="menu-row">
          <span class="item-name">{item.name}</span>
          {#if item.free}
            <span class="item-free">Free</span>
          {:else if item.price}
            <span class="item-price">{item.price}</span>
          {/if}
        </div>
      {/each}
    </div>

    <div class="extras-divider"></div>

    <div class="extras-col">
      <p class="eyebrow-red">FRESHLY MADE</p>
      <h2 class="extras-title">Natural Drinks</h2>
      {#each drinks as item}
        <div class="menu-row">
          <span class="item-name">{item.name}</span>
          <span class="item-price">{item.price}</span>
        </div>
      {/each}
    </div>

  </div>
</section>

<!-- ── CTA ── -->
<section class="cta-section">
  <div class="cta-pill photo-bg" style="background-image:url('/photos/cta-bg.jpg')">
    <div class="cta-overlay"></div>
    <div class="cta-text">
      <span class="cta-line cream">Good food,</span>
      <div class="cta-line cta-line-pair">
        <span class="amber">good vibes,</span>
        <span class="cream">every day.</span>
      </div>
    </div>
    <a href="/contact" class="cta-btn">Come Visit Us</a>
  </div>
</section>

<style>
/* ── SHARED ── */
.menu-inner {
  max-width: var(--container);
  margin: 0 auto;
}

.eyebrow-red {
  font-family: var(--font-body);
  font-size: 13px;
  letter-spacing: 1.8px;
  text-transform: uppercase;
  color: var(--red);
}
.eyebrow-amber {
  font-family: var(--font-body);
  font-size: 13px;
  letter-spacing: 1.8px;
  text-transform: uppercase;
  color: var(--amber);
}

/* ── HEADING ── */
.menu-heading {
  background: #fffff4;
  padding: clamp(56px, 7vw, 100px) clamp(24px, 5.6vw, 80px) clamp(32px, 4vw, 56px);
  text-align: center;
}
.menu-title {
  font-family: var(--font-display);
  font-size: clamp(48px, 7vw, 80px);
  line-height: 1.1;
  color: var(--dark);
}
.menu-hours {
  font-family: var(--font-body);
  font-size: 13px;
  letter-spacing: 1.4px;
  text-transform: uppercase;
  color: var(--dark);
  opacity: 0.45;
  margin-top: 14px;
}

/* ── TABS ── */
.tabs-section {
  background: #fffff4;
  padding: 0 clamp(24px, 5.6vw, 80px);
}
.day-tabs {
  display: flex;
  justify-content: center;
  gap: clamp(16px, 3.5vw, 56px);
  border-bottom: 1px solid rgba(45,26,20,0.12);
  overflow-x: auto;
  scrollbar-width: none;
}
.day-tabs::-webkit-scrollbar { display: none; }
.day-tab {
  font-family: var(--font-body);
  font-weight: 600;
  font-size: 13px;
  letter-spacing: 1.8px;
  color: var(--dark);
  opacity: 0.35;
  padding: 18px 4px;
  border: none;
  border-bottom: 2px solid transparent;
  margin-bottom: -1px;
  white-space: nowrap;
  background: none;
  cursor: pointer;
  transition: opacity 0.18s, border-color 0.18s;
}
.day-tab:hover { opacity: 0.65; }
.day-tab.active { opacity: 1; border-bottom-color: var(--dark); }

/* ── DAILY MENU ── */
.daily-section {
  background: #fffff4;
  padding: clamp(56px, 6vw, 96px) clamp(24px, 5.6vw, 80px);
}
.menu-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 56px 80px;
  align-items: start;
}

/* ── SHARED CATEGORY BLOCK ── */
.menu-cat { display: flex; flex-direction: column; }

.cat-label {
  font-family: var(--font-label);
  font-weight: 600;
  font-size: 11px;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--amber);
  padding-bottom: 14px;
  border-bottom: 1px solid rgba(45,26,20,0.14);
}
.cat-amber { color: var(--amber); border-bottom-color: rgba(247,240,220,0.15); }

.menu-row {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  gap: 16px;
  padding: 13px 0;
  border-bottom: 1px solid rgba(45,26,20,0.07);
}
.row-dark { border-bottom-color: rgba(247,240,220,0.08); }

.item-name {
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 1.5;
  color: var(--dark);
}
.name-cream { color: var(--cream); }

.item-price {
  font-family: var(--font-body);
  font-size: 15px;
  color: var(--dark);
  opacity: 0.5;
  white-space: nowrap;
  flex-shrink: 0;
}
.price-cream { color: var(--cream); opacity: 0.65; }

.item-free {
  font-family: var(--font-body);
  font-size: 11px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: #5a8a5a;
  white-space: nowrap;
  flex-shrink: 0;
}

/* ── DONE TO ORDER ── */
.dto-section {
  background: var(--bg-dark);
  padding: clamp(56px, 6vw, 96px) clamp(24px, 5.6vw, 80px);
}
.dto-head { margin-bottom: 48px; }
.dto-title {
  font-family: var(--font-display);
  font-size: clamp(36px, 5vw, 64px);
  line-height: 1.1;
  color: var(--cream);
  margin-top: 8px;
}
.dto-pair {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 48px 80px;
  align-items: start;
  margin-bottom: 48px;
}
.grills-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0 80px;
}

/* ── SIDES & DRINKS ── */
.extras-section {
  background: #fffff4;
  padding: clamp(56px, 6vw, 96px) clamp(24px, 5.6vw, 80px);
}
.extras-row {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 80px;
  align-items: start;
}
.extras-divider {
  width: 1px;
  background: rgba(45,26,20,0.12);
  align-self: stretch;
  min-height: 100px;
}
.extras-col { display: flex; flex-direction: column; }
.extras-title {
  font-family: var(--font-display);
  font-size: clamp(32px, 4vw, 52px);
  line-height: 1.1;
  color: var(--dark);
  margin: 8px 0 32px;
}

/* ── CTA ── */
.cta-section {
  background: #fffff4;
  padding: 0 clamp(24px, 5.6vw, 80px) var(--section-pad);
}
.cta-pill {
  position: relative;
  max-width: var(--container);
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
.cta-line-pair {
  display: flex;
  gap: 0.28em;
  align-items: baseline;
  justify-content: center;
}
.cta-line-pair .amber { color: var(--amber); }
.cta-line-pair .cream { color: var(--cream); }
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
@media (max-width: 960px) {
  .menu-grid { grid-template-columns: 1fr; gap: 48px; }
  .dto-pair  { grid-template-columns: 1fr; gap: 48px; }
  .grills-grid { grid-template-columns: 1fr; }
  .extras-row { grid-template-columns: 1fr; gap: 48px; }
  .extras-divider { width: 100%; height: 1px; min-height: unset; }
}
@media (max-width: 680px) {
  .cta-pill { border-radius: 40px; padding: 56px 32px; }
  .day-tabs { gap: 16px; }
}
@media (max-width: 480px) {
  .cta-section { padding-left: 0; padding-right: 0; }
  .cta-pill { border-radius: 0; }
}
</style>
