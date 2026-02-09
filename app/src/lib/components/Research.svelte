<script lang="ts">
  const journals = [
    { name: 'The Lancet', shortName: 'Lancet' },
    { name: 'Brain', shortName: 'Brain' },
    { name: 'Indian Pediatrics', shortName: 'Indian Ped.' },
    { name: 'Frontiers', shortName: 'Frontiers' },
  ];

  const publications = [
    {
      title: 'Clinical and molecular spectrum associated with Polymerase-γ related disorders',
      journal: 'Journal of Child Neurology',
      year: '2022',
      type: 'Research Paper',
    },
    {
      title: 'Consensus Statement on Diagnosis and Management of Febrile Seizures',
      journal: 'Indian Pediatrics',
      year: '2021',
      type: 'Consensus Statement',
    },
    {
      title: 'Neurological Manifestations of COVID-19 in Children',
      journal: 'Brain & Development',
      year: '2021',
      type: 'Research Paper',
    },
    {
      title: 'Standard of Care Guidelines for Muscular Dystrophies in India',
      journal: 'Indian Academy of Neurology',
      year: '2020',
      type: 'Guidelines',
    },
  ];
</script>

<section id="research" class="research section">
  <div class="container">
    <div class="section-header">
      <h2>Contributing to Global Knowledge</h2>
      <p class="section-subtitle">Research that shapes how we care for children with neurological conditions.</p>
    </div>

    <div class="journals-bar">
      <p class="journals-label">Featured In</p>
      <div class="journals-logos">
        {#each journals as journal}
          <div class="journal-badge">
            <span class="journal-name">{journal.shortName}</span>
          </div>
        {/each}
      </div>
    </div>

    <div class="publications-grid">
      <h3 class="publications-heading">Recent Publications</h3>
      <div class="publications-list">
        {#each publications as pub, i}
          <article class="publication-card" style="animation-delay: {i * 0.1}s">
            <div class="pub-type">{pub.type}</div>
            <h4 class="pub-title">{pub.title}</h4>
            <div class="pub-meta">
              <span class="pub-journal">{pub.journal}</span>
              <span class="pub-year">{pub.year}</span>
            </div>
            <button class="pub-link" type="button" aria-label="View publication">
              <svg width="16" height="16" viewBox="0 0 16 16" fill="none" aria-hidden="true">
                <path d="M4 12L12 4M12 4H5M12 4V11" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </button>
          </article>
        {/each}
      </div>
    </div>

    <div class="research-cta">
      <a href="#research" class="btn btn-secondary">
        View All 20+ Publications
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
          <path d="M6 12L10 8L6 4" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </a>
    </div>
  </div>
</section>

<style>
  .research {
    background: var(--warm-white);
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

  .journals-bar {
    background: color-mix(in srgb, var(--color-primary) 8%, var(--surface-secondary));
    border-radius: var(--radius-lg);
    padding: var(--space-lg);
    margin-bottom: var(--space-xl);
    margin-left: auto;
    margin-right: auto;
    text-align: center;
    border: 1px solid var(--border-light);
    max-width: 600px;
  }

  .journals-label {
    font-size: var(--text-sm);
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin-bottom: var(--space-md);
    text-align: center;
  }

  .journals-logos {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    gap: var(--space-md);
  }

  .journal-badge {
    padding: var(--space-sm) var(--space-md);
    background: var(--surface-primary);
    border-radius: var(--radius-sm);
    box-shadow: var(--shadow-sm);
    transition: all var(--transition-fast);
    border: 1px solid var(--border-light);
  }

  .journal-badge:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow-md);
  }

  .journal-name {
    font-family: var(--font-display);
    font-weight: 600;
    color: var(--color-primary);
    font-size: var(--text-base);
  }

  .publications-heading {
    font-size: var(--text-xl);
    margin-bottom: var(--space-lg);
    color: var(--text-primary);
  }

  .publications-list {
    display: grid;
    grid-template-columns: 1fr;
    gap: var(--space-md);
  }

  @media (min-width: 768px) {
    .publications-list {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  .publication-card {
    background: var(--surface-primary);
    border-radius: var(--radius-md);
    padding: var(--space-lg);
    border-left: 4px solid var(--color-secondary);
    box-shadow: var(--shadow-sm);
    transition: all var(--transition-base);
    position: relative;
    opacity: 0;
    animation: fade-up 0.5s ease-out forwards;
    border: 1px solid var(--border-light);
    border-left: 4px solid var(--color-secondary);
  }

  .publication-card:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow-md);
  }

  .pub-type {
    display: inline-block;
    font-size: var(--text-xs);
    text-transform: uppercase;
    letter-spacing: 0.05em;
    color: var(--color-tertiary);
    background: color-mix(in srgb, var(--color-tertiary) 15%, transparent);
    padding: 4px 8px;
    border-radius: var(--radius-sm);
    margin-bottom: var(--space-sm);
  }

  .pub-title {
    font-size: var(--text-base);
    font-weight: 600;
    color: var(--text-primary);
    line-height: 1.4;
    margin-bottom: var(--space-sm);
    padding-right: var(--space-xl);
  }

  .pub-meta {
    display: flex;
    gap: var(--space-sm);
    font-size: var(--text-sm);
    color: var(--text-muted);
  }

  .pub-journal {
    font-weight: 500;
  }

  .pub-year {
    opacity: 0.7;
  }

  .pub-link {
    position: absolute;
    top: var(--space-md);
    right: var(--space-md);
    width: 32px;
    height: 32px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: var(--surface-secondary);
    border: 1px solid var(--border-light);
    border-radius: var(--radius-sm);
    color: var(--color-primary);
    cursor: pointer;
    transition: all var(--transition-fast);
  }

  .pub-link:hover {
    background: var(--color-primary);
    color: var(--warm-white);
    border-color: var(--color-primary);
  }

  .research-cta {
    text-align: center;
    margin-top: var(--space-xl);
  }
</style>
