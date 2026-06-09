<script>
  /** @type {string} */  export let title;
  /** @type {string} */  export let description;
  /** @type {string} */  export let canonical;
  /** @type {string} */  export let image = 'https://seasideparadise.ky/photos/hero.jpg';
  /** @type {any[]} */   export let jsonLd = [];

  const siteName  = 'Seaside Paradise Restaurant';
  const siteUrl   = 'https://seasideparadise.ky';
  const fullTitle = title.includes(siteName) ? title : `${title} | ${siteName}`;
  const canonUrl  = `${siteUrl}${canonical}`;
</script>

<svelte:head>
  <title>{fullTitle}</title>
  <meta name="description" content={description} />
  <link rel="canonical" href={canonUrl} />

  <!-- Open Graph -->
  <meta property="og:type"        content="website" />
  <meta property="og:site_name"   content={siteName} />
  <meta property="og:url"         content={canonUrl} />
  <meta property="og:title"       content={fullTitle} />
  <meta property="og:description" content={description} />
  <meta property="og:image"       content={image} />
  <meta property="og:image:width"  content="1200" />
  <meta property="og:image:height" content="630" />
  <meta property="og:locale"      content="en_KY" />

  <!-- Twitter / X -->
  <meta name="twitter:card"        content="summary_large_image" />
  <meta name="twitter:title"       content={fullTitle} />
  <meta name="twitter:description" content={description} />
  <meta name="twitter:image"       content={image} />

  <!-- Geo -->
  <meta name="geo.region"      content="KY-GC" />
  <meta name="geo.placename"   content="Bodden Town, Grand Cayman" />
  <meta name="geo.position"    content="19.2930;-81.2480" />
  <meta name="ICBM"            content="19.2930, -81.2480" />

  <!-- JSON-LD -->
  {#each jsonLd as schema}
    {@html `<script type="application/ld+json">${JSON.stringify(schema)}<\/script>`}
  {/each}
</svelte:head>
