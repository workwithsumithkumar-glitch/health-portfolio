<script lang="ts">
  import FloatingParticles from './FloatingParticles.svelte';
  import NeuralLines from './NeuralLines.svelte';
</script>

<section id="home" class="hero">
  <NeuralLines />
  <FloatingParticles />

  <div class="hero-container">
    <div class="hero-content">
      <p class="hero-tagline">Pediatric Neurologist</p>
      <h1 class="hero-headline">
        Every brain tells<br/>
        <span class="highlight">a story</span>
      </h1>
      <p class="hero-subheadline">
        Specialized pediatric neurology care in Indore. 25+ years helping children thrive with compassion, expertise, and hope.
      </p>
      <div class="hero-ctas">
        <a href="#contact" class="btn btn-primary">Book Consultation</a>
        <a href="#expertise" class="btn btn-secondary">
          Explore Conditions
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
            <path d="M6 12L10 8L6 4" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </a>
      </div>
    </div>

    <div class="hero-image">
      <div class="image-blob">
        <img
          src="/images/hero/dr-dubey-portrait.webp"
          alt="Dr. Rachana Dubey - Pediatric Neurologist"
          class="hero-photo"
          loading="eager"
          fetchpriority="high"
        />
      </div>
      <div class="image-decoration"></div>
    </div>
  </div>

  <div class="scroll-indicator">
    <span>Scroll to explore</span>
    <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
      <path d="M12 5V19M12 19L5 12M12 19L19 12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  </div>
</section>

<style>
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    background: var(--gradient-hero);
    overflow: hidden;
    padding-top: 100px;
  }

  .hero-container {
    position: relative;
    z-index: 2;
    width: 100%;
    max-width: var(--container-wide);
    margin: 0 auto;
    padding: 0 var(--space-md);
    display: grid;
    grid-template-columns: 1fr;
    gap: var(--space-xl);
    align-items: center;
  }

  @media (min-width: 768px) {
    .hero-container {
      padding: 0 var(--space-lg);
      grid-template-columns: 1fr 1fr;
    }
  }

  .hero-content {
    text-align: center;
  }

  @media (min-width: 768px) {
    .hero-content {
      text-align: left;
    }
  }

  .hero-tagline {
    font-family: var(--font-accent);
    font-size: var(--text-xl);
    color: var(--color-primary);
    margin-bottom: var(--space-sm);
  }

  .hero-headline {
    font-size: var(--text-5xl);
    font-weight: 400;
    margin-bottom: var(--space-md);
    line-height: 1.1;
  }

  .hero-headline .highlight {
    color: var(--color-secondary);
    font-style: italic;
  }

  .hero-subheadline {
    font-size: var(--text-lg);
    color: var(--text-secondary);
    margin-bottom: var(--space-lg);
    max-width: 480px;
  }

  @media (min-width: 768px) {
    .hero-subheadline {
      margin-left: 0;
      margin-right: auto;
    }
  }

  .hero-ctas {
    display: flex;
    flex-direction: column;
    gap: var(--space-md);
    align-items: center;
  }

  @media (min-width: 768px) {
    .hero-ctas {
      flex-direction: row;
      justify-content: flex-start;
    }
  }

  .hero-image {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .image-blob {
    position: relative;
    width: 300px;
    height: 360px;
    border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow:
      var(--shadow-lg),
      0 0 60px rgba(154, 107, 158, 0.15),
      0 0 100px rgba(94, 234, 234, 0.1);
    overflow: hidden;
    border: 3px solid rgba(255, 255, 255, 0.8);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  .image-blob:hover {
    transform: scale(1.02);
    box-shadow:
      var(--shadow-lg),
      0 0 80px rgba(154, 107, 158, 0.2),
      0 0 120px rgba(94, 234, 234, 0.15);
  }

  @media (min-width: 768px) {
    .image-blob {
      width: 380px;
      height: 450px;
    }
  }

  @media (min-width: 1024px) {
    .image-blob {
      width: 420px;
      height: 500px;
    }
  }

  .hero-photo {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center top;
    border-radius: inherit;
  }

  .image-decoration {
    position: absolute;
    width: 120px;
    height: 120px;
    background: var(--gradient-hope);
    border-radius: 50%;
    bottom: -20px;
    right: -20px;
    opacity: 0.6;
    z-index: -1;
    animation: float 6s ease-in-out infinite;
  }

  .scroll-indicator {
    position: absolute;
    bottom: var(--space-lg);
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--space-sm);
    color: var(--color-primary);
    font-size: var(--text-sm);
    opacity: 0.7;
    animation: bounce 2s ease-in-out infinite;
  }

  @keyframes bounce {
    0%, 100% { transform: translateX(-50%) translateY(0); }
    50% { transform: translateX(-50%) translateY(8px); }
  }

  .scroll-indicator svg {
    transform: rotate(180deg);
  }
</style>
