<script lang="ts">
  import Navigation from './lib/components/Navigation.svelte';
  import Hero from './lib/components/Hero.svelte';
  import TrustBar from './lib/components/TrustBar.svelte';
  import Expertise from './lib/components/Expertise.svelte';
  import Story from './lib/components/Story.svelte';
  import GlobalTraining from './lib/components/GlobalTraining.svelte';
  import Gallery from './lib/components/Gallery.svelte';
  import Research from './lib/components/Research.svelte';
  import Testimonials from './lib/components/Testimonials.svelte';
  import Contact from './lib/components/Contact.svelte';
  import Footer from './lib/components/Footer.svelte';
  import BackToTop from './lib/components/BackToTop.svelte';
</script>

<a href="#main-content" class="skip-link">Skip to main content</a>

<Navigation />

<main id="main-content">
  <Hero />
  <TrustBar />
  <Expertise />
  <Story />
  <GlobalTraining />
  <Gallery />
  <Research />
  <Testimonials />
  <Contact />
</main>

<Footer />

<BackToTop />

<style>
  :global(#app) {
    width: 100%;
    max-width: none;
    margin: 0;
    padding: 0;
    text-align: left;
  }

  main {
    min-height: 100vh;
  }
</style>
