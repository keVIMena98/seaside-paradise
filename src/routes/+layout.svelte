<script>
  import '../app.css';
  import Navbar from '$lib/components/Navbar.svelte';
  import Footer from '$lib/components/Footer.svelte';
  import { inject } from '@vercel/analytics';
  inject();
</script>

<Navbar />
<main>
  <slot />
</main>
<Footer />
