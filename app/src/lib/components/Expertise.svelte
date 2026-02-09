<script lang="ts">
  const conditions = [
    {
      id: 'epilepsy',
      icon: 'zap',
      title: 'Epilepsy & Seizures',
      tagline: 'When the brain speaks unexpectedly',
      description: 'Comprehensive diagnosis and management of all seizure types, from febrile seizures to complex epilepsy syndromes.',
      color: 'var(--color-secondary)',
    },
    {
      id: 'autism',
      icon: 'brain',
      title: 'Autism Spectrum',
      tagline: 'Understanding unique minds',
      description: 'Early identification, developmental assessments, and holistic care plans for children on the autism spectrum.',
      color: 'var(--color-tertiary)',
    },
    {
      id: 'muscular',
      icon: 'muscle',
      title: 'Muscular Disorders',
      tagline: 'Strength in different forms',
      description: 'Specialized care for muscular dystrophies, myopathies, and neuromuscular conditions affecting children.',
      color: 'var(--color-accent)',
    },
    {
      id: 'movement',
      icon: 'activity',
      title: 'Movement Disorders',
      tagline: 'When motion needs guidance',
      description: 'Expert management of involuntary movements, tics, tremors, and coordination difficulties.',
      color: 'var(--color-soft)',
    },
    {
      id: 'developmental',
      icon: 'growth',
      title: 'Developmental Delays',
      tagline: 'Every milestone matters',
      description: 'Thorough evaluation of developmental milestones with personalized intervention strategies.',
      color: 'var(--color-primary)',
    },
    {
      id: 'rare',
      icon: 'dna',
      title: 'Rare Conditions',
      tagline: 'Even uncommon stories deserve care',
      description: 'Diagnosis and management of rare neurological conditions with access to global expertise.',
      color: 'var(--color-light)',
    },
  ];
</script>

<section id="expertise" class="expertise section">
  <div class="container">
    <div class="section-header">
      <h2>Conditions We Understand</h2>
      <p class="section-subtitle">Every child's journey is unique. We're here to guide you with expertise and compassion.</p>
    </div>

    <div class="conditions-grid">
      {#each conditions as condition, i}
        <div class="condition-card" style="--card-color: {condition.color}; animation-delay: {i * 0.1}s">
          <div class="card-icon">
            {#if condition.icon === 'zap'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/>
              </svg>
            {:else if condition.icon === 'brain'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M9.5 2A2.5 2.5 0 0 1 12 4.5v15a2.5 2.5 0 0 1-4.96.44 2.5 2.5 0 0 1-2.96-3.08 3 3 0 0 1-.34-5.58 2.5 2.5 0 0 1 1.32-4.24 2.5 2.5 0 0 1 1.98-3A2.5 2.5 0 0 1 9.5 2Z"/>
                <path d="M14.5 2A2.5 2.5 0 0 0 12 4.5v15a2.5 2.5 0 0 0 4.96.44 2.5 2.5 0 0 0 2.96-3.08 3 3 0 0 0 .34-5.58 2.5 2.5 0 0 0-1.32-4.24 2.5 2.5 0 0 0-1.98-3A2.5 2.5 0 0 0 14.5 2Z"/>
              </svg>
            {:else if condition.icon === 'muscle'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M6.5 6.5c1.5-1.5 3.5-2 5.5-1.5"/>
                <path d="M17.5 6.5c-1.5-1.5-3.5-2-5.5-1.5"/>
                <path d="M6.5 17.5c1.5 1.5 3.5 2 5.5 1.5"/>
                <path d="M17.5 17.5c-1.5 1.5-3.5 2-5.5 1.5"/>
                <circle cx="12" cy="12" r="3"/>
                <path d="M12 2v4M12 18v4M2 12h4M18 12h4"/>
              </svg>
            {:else if condition.icon === 'activity'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/>
              </svg>
            {:else if condition.icon === 'growth'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M12 20V10"/>
                <path d="M18 20V4"/>
                <path d="M6 20v-4"/>
              </svg>
            {:else if condition.icon === 'dna'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M2 15c6.667-6 13.333 0 20-6"/>
                <path d="M9 22c1.798-1.998 2.518-3.995 2.807-5.993"/>
                <path d="M15 2c-1.798 1.998-2.518 3.995-2.807 5.993"/>
                <path d="M17 6l-2.5-2.5"/>
                <path d="M14 8l-3-3"/>
                <path d="M7 18l2.5 2.5"/>
                <path d="M3.5 14.5l.5.5"/>
                <path d="M20 9.5l.5.5"/>
                <path d="M10 16l-3 3"/>
              </svg>
            {/if}
          </div>
          <h3 class="card-title">{condition.title}</h3>
          <p class="card-tagline">{condition.tagline}</p>
          <p class="card-description">{condition.description}</p>
          <a href="#{condition.id}" class="card-link">
            Learn more
            <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
              <path d="M6 12L10 8L6 4" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .expertise {
    background: var(--surface-secondary);
  }

  .section-header {
    text-align: center;
    margin-bottom: var(--space-xl);
  }

  .section-header h2 {
    margin-bottom: var(--space-sm);
  }

  .section-subtitle {
    font-size: var(--text-lg);
    color: var(--text-secondary);
    max-width: 600px;
    margin: 0 auto;
  }

  .conditions-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: var(--space-lg);
  }

  @media (min-width: 640px) {
    .conditions-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (min-width: 1024px) {
    .conditions-grid {
      grid-template-columns: repeat(3, 1fr);
    }
  }

  .condition-card {
    background: var(--surface-primary);
    border-radius: var(--radius-lg);
    padding: var(--space-lg);
    box-shadow: var(--shadow-sm);
    transition: all var(--transition-base);
    position: relative;
    overflow: hidden;
    opacity: 0;
    animation: fade-up 0.6s ease-out forwards;
    border: 1px solid var(--border-light);
  }

  .condition-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: var(--card-color);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform var(--transition-base);
  }

  .condition-card:hover {
    transform: translateY(-4px);
    box-shadow: var(--shadow-lg);
  }

  .condition-card:hover::before {
    transform: scaleX(1);
  }

  .card-icon {
    width: 48px;
    height: 48px;
    padding: 10px;
    background: color-mix(in srgb, var(--card-color) 15%, transparent);
    border-radius: var(--radius-md);
    color: var(--card-color);
    margin-bottom: var(--space-md);
  }

  .card-icon svg {
    width: 100%;
    height: 100%;
  }

  .card-title {
    font-size: var(--text-xl);
    font-weight: 600;
    margin-bottom: var(--space-xs);
    color: var(--text-primary);
  }

  .card-tagline {
    font-family: var(--font-accent);
    font-size: var(--text-lg);
    color: var(--card-color);
    margin-bottom: var(--space-sm);
  }

  .card-description {
    font-size: var(--text-base);
    color: var(--text-secondary);
    line-height: 1.6;
    margin-bottom: var(--space-md);
  }

  .card-link {
    display: inline-flex;
    align-items: center;
    gap: var(--space-xs);
    font-weight: 600;
    color: var(--color-primary);
    transition: all var(--transition-fast);
  }

  .card-link:hover {
    color: var(--color-secondary);
    gap: var(--space-sm);
  }

  .card-link svg {
    transition: transform var(--transition-fast);
  }

  .card-link:hover svg {
    transform: translateX(4px);
  }
</style>
