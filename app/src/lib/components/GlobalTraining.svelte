<script lang="ts">
  const locations = [
    {
      id: 'cleveland',
      name: 'Cleveland Clinic',
      country: 'USA',
      year: '2010',
      training: 'Epilepsy & Electrophysiology',
      description: 'Advanced training in epilepsy monitoring and electrophysiology techniques',
      image: '/images/training/cleveland-clinic-usa-2010.png',
      flag: '🇺🇸',
    },
    {
      id: 'delhi',
      name: 'AIIMS',
      country: 'New Delhi',
      year: '2015',
      training: 'D.M. Pediatric Neurology',
      description: "India's premier medical institution for specialized neurology training",
      image: '/images/training/aiims-delhi-2015.png',
      flag: '🇮🇳',
    },
    {
      id: 'paris',
      name: 'Institut de Myologie',
      country: 'Paris, France',
      year: '2017',
      training: 'Muscle Disorders',
      description: 'Specialized fellowship in neuromuscular disorders and myopathies',
      image: '/images/training/paris-myologie-2017.png',
      flag: '🇫🇷',
    },
    {
      id: 'cambridge',
      name: 'Cambridge University',
      country: 'United Kingdom',
      year: '2018',
      training: 'Neonatal EEG',
      description: 'Fellowship in neonatal brain monitoring and EEG interpretation',
      image: '/images/training/cambridge-uk-2018.png',
      flag: '🇬🇧',
    },
    {
      id: 'italy',
      name: 'San Servolo Island',
      country: 'Venice, Italy',
      year: '2018',
      training: 'ILAE Pediatric Epilepsy',
      description: 'International League Against Epilepsy advanced pediatric program',
      image: '/images/training/italy-san-servolo-2018.png',
      flag: '🇮🇹',
    },
  ];
</script>

<section class="global-training section">
  <div class="container">
    <div class="section-header">
      <p class="section-preheading">Global Expertise</p>
      <h2>Trained Across <span class="highlight">4 Continents</span></h2>
      <p class="section-subtitle">Learning from the world's best to serve you better</p>
    </div>

    <div class="training-grid">
      {#each locations as loc, i}
        <article class="training-card" style="animation-delay: {i * 0.1}s">
          <div class="card-image">
            <img src={loc.image} alt="{loc.name}, {loc.country}" loading="lazy" />
            <div class="card-overlay">
              <span class="card-year">{loc.year}</span>
            </div>
          </div>
          <div class="card-content">
            <div class="card-header">
              <span class="card-flag">{loc.flag}</span>
              <div class="card-location">
                <h3 class="card-name">{loc.name}</h3>
                <p class="card-country">{loc.country}</p>
              </div>
            </div>
            <p class="card-training">{loc.training}</p>
            <p class="card-description">{loc.description}</p>
          </div>
        </article>
      {/each}
    </div>

    <div class="training-summary">
      <div class="summary-item">
        <span class="summary-number">5</span>
        <span class="summary-label">Institutions</span>
      </div>
      <div class="summary-divider"></div>
      <div class="summary-item">
        <span class="summary-number">4</span>
        <span class="summary-label">Countries</span>
      </div>
      <div class="summary-divider"></div>
      <div class="summary-item">
        <span class="summary-number">3</span>
        <span class="summary-label">Continents</span>
      </div>
    </div>
  </div>
</section>

<style>
  .global-training {
    background: linear-gradient(180deg, var(--surface-secondary) 0%, var(--warm-white) 100%);
  }

  .section-header {
    text-align: center;
    margin-bottom: var(--space-xl);
  }

  .section-preheading {
    font-family: var(--font-accent);
    font-size: var(--text-xl);
    color: var(--color-primary);
    margin-bottom: var(--space-xs);
  }

  .section-header h2 {
    font-size: var(--text-3xl);
    margin-bottom: var(--space-sm);
  }

  .section-header .highlight {
    color: var(--color-secondary);
    font-style: italic;
  }

  .section-subtitle {
    font-size: var(--text-lg);
    color: var(--text-secondary);
    max-width: 500px;
    margin: 0 auto;
  }

  /* Training Grid */
  .training-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: var(--space-lg);
  }

  @media (min-width: 640px) {
    .training-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (min-width: 1024px) {
    .training-grid {
      grid-template-columns: repeat(3, 1fr);
    }

    /* Make the last 2 cards span center */
    .training-card:nth-child(4) {
      grid-column: 1 / 2;
    }

    .training-card:nth-child(5) {
      grid-column: 2 / 3;
    }
  }

  @media (min-width: 1200px) {
    .training-grid {
      grid-template-columns: repeat(5, 1fr);
    }

    .training-card:nth-child(4),
    .training-card:nth-child(5) {
      grid-column: auto;
    }
  }

  /* Training Card */
  .training-card {
    background: var(--surface-primary);
    border-radius: var(--radius-lg);
    overflow: hidden;
    box-shadow: var(--shadow-sm);
    border: 1px solid var(--border-light);
    transition: all var(--transition-base);
    opacity: 0;
    animation: fade-up 0.5s ease-out forwards;
  }

  .training-card:hover {
    transform: translateY(-4px);
    box-shadow: var(--shadow-lg);
  }

  .card-image {
    position: relative;
    height: 180px;
    overflow: hidden;
  }

  .card-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.4s ease;
  }

  .training-card:hover .card-image img {
    transform: scale(1.05);
  }

  .card-overlay {
    position: absolute;
    top: var(--space-sm);
    right: var(--space-sm);
  }

  .card-year {
    background: rgba(0, 0, 0, 0.6);
    color: white;
    padding: 4px 10px;
    border-radius: var(--radius-full);
    font-size: var(--text-xs);
    font-weight: 600;
    backdrop-filter: blur(4px);
  }

  .card-content {
    padding: var(--space-md);
  }

  .card-header {
    display: flex;
    align-items: flex-start;
    gap: var(--space-sm);
    margin-bottom: var(--space-sm);
  }

  .card-flag {
    font-size: var(--text-2xl);
    line-height: 1;
  }

  .card-location {
    flex: 1;
  }

  .card-name {
    font-size: var(--text-base);
    font-weight: 600;
    color: var(--text-primary);
    line-height: 1.2;
    margin-bottom: 2px;
  }

  .card-country {
    font-size: var(--text-sm);
    color: var(--text-muted);
  }

  .card-training {
    font-size: var(--text-sm);
    font-weight: 600;
    color: var(--color-primary);
    margin-bottom: var(--space-xs);
    padding: 4px 8px;
    background: color-mix(in srgb, var(--color-primary) 10%, transparent);
    border-radius: var(--radius-sm);
    display: inline-block;
  }

  .card-description {
    font-size: var(--text-sm);
    color: var(--text-secondary);
    line-height: 1.5;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }

  /* Summary Bar */
  .training-summary {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: var(--space-lg);
    margin-top: var(--space-xl);
    padding: var(--space-lg);
    background: color-mix(in srgb, var(--color-primary) 8%, var(--surface-primary));
    border-radius: var(--radius-lg);
    border: 1px solid var(--border-light);
  }

  .summary-item {
    text-align: center;
  }

  .summary-number {
    display: block;
    font-family: var(--font-display);
    font-size: var(--text-3xl);
    font-weight: 600;
    color: var(--color-secondary);
    line-height: 1;
  }

  .summary-label {
    font-size: var(--text-sm);
    color: var(--text-muted);
  }

  .summary-divider {
    width: 1px;
    height: 40px;
    background: var(--border-light);
  }

  @media (max-width: 480px) {
    .training-summary {
      gap: var(--space-md);
      padding: var(--space-md);
    }

    .summary-number {
      font-size: var(--text-2xl);
    }

    .summary-divider {
      height: 30px;
    }
  }
</style>
