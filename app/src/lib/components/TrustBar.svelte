<script lang="ts">
  import { onMount } from 'svelte';

  let visible = $state(false);
  let countersStarted = $state(false);

  const metrics = [
    { value: 'AIIMS', label: 'Delhi', sublabel: 'D.M. Pediatric Neurology', icon: 'graduation' },
    { value: '25+', label: 'Years', sublabel: 'Experience', icon: 'calendar', isNumber: true, target: 25 },
    { value: '20+', label: 'Papers', sublabel: 'Published Research', icon: 'document', isNumber: true, target: 20 },
    { value: '4', label: 'Countries', sublabel: 'International Training', icon: 'globe', isNumber: true, target: 4 },
    { value: 'ICNA', label: 'Member', sublabel: 'Global Network', icon: 'network' },
  ];

  const recognitionPhotos = [
    { src: '/images/awards/ilae-eeg-school-kochi-2020.png', title: 'ILAE EEG School - Kochi 2020' },
    { src: '/images/conferences/world-neurology-congress-2023.png', title: 'World Neurology Congress 2023' },
    { src: '/images/conferences/neurology-advances-2024.png', title: 'Neurology Advances 2024' },
    { src: '/images/conferences/ilae-35th-congress-group.png', title: 'ILAE 35th Congress' },
    { src: '/images/dignitaries/medical-board-meeting.png', title: 'Medical Board Meeting' },
  ];

  let displayValues = $state(metrics.map(m => m.isNumber ? '0' : m.value));

  onMount(() => {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting && !countersStarted) {
            visible = true;
            countersStarted = true;
            animateCounters();
          }
        });
      },
      { threshold: 0.3 }
    );

    const el = document.querySelector('.trust-bar');
    if (el) observer.observe(el);

    return () => observer.disconnect();
  });

  function animateCounters() {
    metrics.forEach((metric, index) => {
      if (metric.isNumber && metric.target) {
        let current = 0;
        const increment = metric.target / 30;
        const interval = setInterval(() => {
          current += increment;
          if (current >= metric.target) {
            current = metric.target;
            clearInterval(interval);
          }
          displayValues[index] = Math.floor(current) + (metric.value.includes('+') ? '+' : '');
        }, 50);
      }
    });
  }
</script>

<section class="trust-bar" class:visible>
  <div class="container">
    <div class="trust-grid">
      {#each metrics as metric, i}
        <div class="trust-item" style="animation-delay: {i * 0.1}s">
          <div class="trust-icon">
            {#if metric.icon === 'graduation'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M22 10v6M2 10l10-5 10 5-10 5z"/>
                <path d="M6 12v5c3 3 9 3 12 0v-5"/>
              </svg>
            {:else if metric.icon === 'calendar'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <rect x="3" y="4" width="18" height="18" rx="2" ry="2"/>
                <line x1="16" y1="2" x2="16" y2="6"/>
                <line x1="8" y1="2" x2="8" y2="6"/>
                <line x1="3" y1="10" x2="21" y2="10"/>
              </svg>
            {:else if metric.icon === 'document'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/>
                <polyline points="14 2 14 8 20 8"/>
                <line x1="16" y1="13" x2="8" y2="13"/>
                <line x1="16" y1="17" x2="8" y2="17"/>
              </svg>
            {:else if metric.icon === 'globe'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <circle cx="12" cy="12" r="10"/>
                <line x1="2" y1="12" x2="22" y2="12"/>
                <path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/>
              </svg>
            {:else if metric.icon === 'network'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <circle cx="12" cy="5" r="3"/>
                <circle cx="5" cy="19" r="3"/>
                <circle cx="19" cy="19" r="3"/>
                <line x1="12" y1="8" x2="5" y2="16"/>
                <line x1="12" y1="8" x2="19" y2="16"/>
              </svg>
            {/if}
          </div>
          <div class="trust-value">{displayValues[i]}</div>
          <div class="trust-label">{metric.label}</div>
          <div class="trust-sublabel">{metric.sublabel}</div>
        </div>
      {/each}
    </div>

    <!-- Recognition Strip -->
    <div class="recognition-strip">
      <h3 class="recognition-title">Recognition & Achievements</h3>
      <div class="recognition-scroll">
        {#each recognitionPhotos as photo}
          <div class="recognition-item">
            <img src={photo.src} alt={photo.title} loading="lazy" />
            <span class="recognition-caption">{photo.title}</span>
          </div>
        {/each}
      </div>
    </div>
  </div>
</section>

<style>
  .trust-bar {
    background: color-mix(in srgb, var(--color-primary) 8%, var(--warm-white));
    padding: var(--space-xl) 0;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.6s ease-out;
  }

  .trust-bar.visible {
    opacity: 1;
    transform: translateY(0);
  }

  .trust-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: var(--space-lg);
  }

  @media (min-width: 768px) {
    .trust-grid {
      grid-template-columns: repeat(5, 1fr);
      gap: var(--space-md);
    }
  }

  .trust-item {
    text-align: center;
    padding: var(--space-md);
    opacity: 0;
    animation: fade-up 0.5s ease-out forwards;
  }

  .trust-item:last-child {
    grid-column: span 2;
  }

  @media (min-width: 768px) {
    .trust-item:last-child {
      grid-column: span 1;
    }
  }

  .trust-icon {
    width: 40px;
    height: 40px;
    margin: 0 auto var(--space-sm);
    color: var(--color-primary);
  }

  .trust-icon svg {
    width: 100%;
    height: 100%;
  }

  .trust-value {
    font-family: var(--font-display);
    font-size: var(--text-2xl);
    font-weight: 600;
    color: var(--color-primary);
    line-height: 1;
  }

  .trust-label {
    font-size: var(--text-base);
    font-weight: 600;
    color: var(--text-primary);
    margin-top: var(--space-xs);
  }

  .trust-sublabel {
    font-size: var(--text-sm);
    color: var(--text-muted);
  }

  /* Recognition Strip */
  .recognition-strip {
    margin-top: var(--space-xl);
    padding-top: var(--space-lg);
    border-top: 1px solid var(--border-light);
  }

  .recognition-title {
    font-family: var(--font-accent);
    font-size: var(--text-lg);
    color: var(--color-primary);
    text-align: center;
    margin-bottom: var(--space-md);
    font-weight: 400;
  }

  .recognition-scroll {
    display: flex;
    gap: var(--space-md);
    overflow-x: auto;
    padding: var(--space-sm) 0;
    scroll-snap-type: x mandatory;
    -webkit-overflow-scrolling: touch;
    scrollbar-width: thin;
    scrollbar-color: var(--color-light) transparent;
  }

  .recognition-scroll::-webkit-scrollbar {
    height: 6px;
  }

  .recognition-scroll::-webkit-scrollbar-track {
    background: transparent;
  }

  .recognition-scroll::-webkit-scrollbar-thumb {
    background: var(--color-light);
    border-radius: 3px;
  }

  .recognition-item {
    flex-shrink: 0;
    width: 200px;
    scroll-snap-align: start;
  }

  .recognition-item img {
    width: 100%;
    height: 130px;
    object-fit: cover;
    border-radius: var(--radius-md);
    box-shadow: var(--shadow-sm);
    transition: all var(--transition-fast);
  }

  .recognition-item:hover img {
    transform: scale(1.03);
    box-shadow: var(--shadow-md);
  }

  .recognition-caption {
    display: block;
    font-size: var(--text-xs);
    color: var(--text-muted);
    text-align: center;
    margin-top: var(--space-xs);
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  @media (min-width: 768px) {
    .recognition-item {
      width: 220px;
    }

    .recognition-item img {
      height: 150px;
    }
  }
</style>
