<script>
  const days = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];

  const menuData = {
    Monday: [
      { name: 'Chicken Soup', price: '$7', desc: 'Homemade chicken soup simmered with local vegetables, dumplings and island spices. A warm, comforting bowl to start your meal.' },
      { name: 'Fry Chicken', price: '$9', desc: 'Golden-fried chicken seasoned Caymanian-style. Crispy on the outside, juicy all the way through. Served with your choice of side.' },
      { name: 'Curry Chicken', price: '$10', desc: 'Tender chicken slow-cooked in a rich Caribbean curry sauce with potatoes and peppers. Served with white rice or rice and peas.' },
    ],
    Tuesday: [
      { name: 'Oxtail', price: '$12', desc: 'Fall-off-the-bone oxtail braised for hours in a rich, dark gravy. Served with rice and peas and fresh coleslaw on the side.' },
      { name: 'Curry Beef', price: '$11', desc: 'Authentic Caribbean curry, melt-in-your-mouth tender.' },
      { name: 'Jerk Chicken', price: '$10', desc: 'Marinated overnight in scotch bonnet, allspice and fresh thyme. Grilled until the skin blisters and the inside stays juicy.' },
      { name: 'BBQ Chicken', price: '$10', desc: 'Smoky, charred chicken glazed with our homemade BBQ sauce. Bold, sticky and full of island flavor every single time.' },
    ],
    Wednesday: [
      { name: 'Brown Stew Fish', price: '$12', desc: 'Fresh local fish braised low and slow in a rich brown gravy with peppers, onions and island spices.' },
      { name: 'Stew Beef', price: '$11', desc: 'Braised beef in rich brown gravy with fresh vegetables.' },
      { name: 'Pepper Steak', price: '$12', desc: 'Beef with peppers and our house pepper sauce.' },
    ],
    Thursday: [
      { name: 'Stew Conch', price: '$12', desc: 'Tender conch stew braised in tomato and island spices.' },
      { name: 'Rondon', price: '$11', desc: 'The Caymanian one-pot — salt fish in coconut milk with breadfruit.' },
      { name: 'Roast Pork', price: '$11', desc: 'Slow-oven-roasted pork seasoned with Caymanian herbs and spices. Tender, moist and deeply flavorful.' },
    ],
    Friday: [
      { name: 'Jerk Pork', price: '$12', desc: 'Pork marinated in jerk spices, grilled over open fire.' },
      { name: 'Jerk Chicken', price: '$10', desc: 'Our most popular grill — full of flavour.' },
      { name: 'Conch & Beans', price: '$12', desc: 'A Caymanian staple — slow cooked with butter beans.' },
    ],
    Saturday: [
      { name: 'Roast Beef', price: '$12', desc: 'Slow-roasted beef seasoned with Caribbean spices. Carved fresh and served with gravy.' },
      { name: 'Stew Chicken', price: '$10', desc: 'Chicken pieces slow-stewed in a savory brown sauce with onions, thyme and local seasonings.' },
      { name: 'Jerk Chicken', price: '$10', desc: 'Marinated overnight in scotch bonnet, allspice and fresh thyme. Grilled until the skin blisters.' },
    ],
  };

  let activeDay = 'Monday';
</script>

<svelte:head>
  <title>Our Daily Rotating Menu — Seaside Paradise Restaurant</title>
</svelte:head>

<!-- HERO -->
<section class="menu-hero">
  <div class="container">
    <span class="label">Discover Our</span>
    <h1 class="display menu-heading">Our Daily<br />Rotating<br />Menu</h1>
    <p class="menu-sub">Fresh every day. Ask us what's hot when you walk in.</p>
  </div>
</section>

<!-- DAY TABS -->
<section class="menu-main">
  <div class="container">
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

    <div class="menu-items" role="tabpanel">
      {#each menuData[activeDay] as item (item.name)}
        <div class="menu-item">
          <div class="item-color-bar"></div>
          <div class="item-body">
            <div class="item-header">
              <h3 class="item-name">{item.name}</h3>
              <span class="item-price">{item.price}</span>
            </div>
            <p class="item-desc">{item.desc}</p>
          </div>
        </div>
      {/each}
    </div>

    <p class="menu-note">Menu changes daily based on what's fresh. Items may vary. Ask us what's available today.</p>
  </div>
</section>

<!-- CTA -->
<section class="menu-cta photo-bg" style="background-image:url('/photos/beach-trees.jpg')">
  <div class="cta-overlay"></div>
  <div class="container cta-content">
    <h2 class="display cta-text">Good food,<br /><em>good vibes,</em><br />every day.</h2>
    <a href="/contact" class="btn btn-outline-cream">Come Visit Us</a>
  </div>
</section>

<style>
/* HERO */
.menu-hero {
  background: var(--offwhite);
  padding: clamp(80px, 10vw, 140px) 0 clamp(48px, 6vw, 80px);
  border-bottom: 1px solid var(--border);
}
.menu-hero .label { display: block; margin-bottom: 12px; }
.menu-heading { font-size: clamp(40px, 7vw, 80px); margin-bottom: 16px; }
.menu-sub { font-size: 16px; color: var(--text-muted); }

/* MENU MAIN */
.menu-main { background: var(--cream); padding: 56px 0; }

.day-tabs {
  display: flex;
  gap: 0;
  border-bottom: 2px solid var(--border);
  margin-bottom: 48px;
  overflow-x: auto;
  scrollbar-width: none;
}
.day-tabs::-webkit-scrollbar { display: none; }

.day-tab {
  font-family: var(--font-label);
  font-weight: 600;
  font-size: 13px;
  letter-spacing: 0.08em;
  padding: 12px 24px;
  color: var(--text-muted);
  border-bottom: 3px solid transparent;
  margin-bottom: -2px;
  transition: color 0.2s, border-color 0.2s;
  white-space: nowrap;
}
.day-tab:hover { color: var(--dark); }
.day-tab.active { color: var(--dark); border-bottom-color: var(--amber); }

.menu-items {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  margin-bottom: 40px;
}

.menu-item {
  background: var(--offwhite);
  display: flex;
  gap: 0;
  border-radius: var(--radius);
  overflow: hidden;
  transition: transform 0.2s;
}
.menu-item:hover { transform: translateY(-2px); }
.item-color-bar { width: 5px; background: var(--amber); flex-shrink: 0; }
.item-body { padding: 20px; }
.item-header { display: flex; justify-content: space-between; align-items: flex-start; gap: 12px; margin-bottom: 10px; }
.item-name { font-family: var(--font-label); font-weight: 600; font-size: 17px; }
.item-price { font-family: var(--font-label); font-size: 16px; color: var(--amber); flex-shrink: 0; font-weight: 600; }
.item-desc { font-size: 14px; color: var(--text-muted); line-height: 1.65; }

.menu-note {
  font-size: 13px;
  color: var(--text-muted);
  font-style: italic;
  text-align: center;
}

/* CTA */
.menu-cta {
  position: relative;
  min-height: 380px;
  display: flex;
  align-items: center;
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

@media (max-width: 900px) {
  .menu-items { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 600px) {
  .menu-items { grid-template-columns: 1fr; }
  .day-tab { padding: 12px 14px; }
}
</style>
