<script lang="ts">
  let selectedCategory = $state('all');
  let lightboxOpen = $state(false);
  let lightboxIndex = $state(0);

  type GalleryItem = {
    id: number;
    src: string;
    category: string;
    title: string;
    location: string;
    year: string;
    description: string;
  };

  const categories = [
    { id: 'all', label: 'All' },
    { id: 'awards', label: 'Awards' },
    { id: 'conferences', label: 'Conferences' },
    { id: 'training', label: 'Training' },
    { id: 'dignitaries', label: 'Dignitaries' },
  ];

  const galleryItems: GalleryItem[] = [
    {
      id: 1,
      src: '/images/awards/ilae-eeg-school-kochi-2020.png',
      category: 'awards',
      title: 'ILAE EEG School Faculty',
      location: 'Kochi, India',
      year: '2020',
      description: '5th ILAE School on EEG with international faculty',
    },
    {
      id: 2,
      src: '/images/conferences/world-neurology-congress-2023.png',
      category: 'conferences',
      title: 'World Neurology Congress',
      location: 'International',
      year: '2023',
      description: 'Presenting research on pediatric neurology advances',
    },
    {
      id: 3,
      src: '/images/conferences/neurology-advances-2024.png',
      category: 'conferences',
      title: 'Neurology Advances Conference',
      location: 'International',
      year: '2024',
      description: 'Speaking on latest developments in child neurology',
    },
    {
      id: 4,
      src: '/images/conferences/ilae-35th-congress-group.png',
      category: 'conferences',
      title: 'ILAE 35th Congress',
      location: 'International',
      year: '2023',
      description: 'With fellow epileptologists from around the world',
    },
    {
      id: 5,
      src: '/images/training/cleveland-clinic-usa-2010.png',
      category: 'training',
      title: 'Cleveland Clinic Training',
      location: 'Ohio, USA',
      year: '2010',
      description: 'Epilepsy & Electrophysiology fellowship',
    },
    {
      id: 6,
      src: '/images/training/paris-myologie-2017.png',
      category: 'training',
      title: 'Institut de Myologie',
      location: 'Paris, France',
      year: '2017',
      description: 'Advanced training in muscle disorders',
    },
    {
      id: 7,
      src: '/images/training/cambridge-uk-2018.png',
      category: 'training',
      title: 'Cambridge Fellowship',
      location: 'Cambridge, UK',
      year: '2018',
      description: 'Neonatal EEG specialization program',
    },
    {
      id: 8,
      src: '/images/training/italy-san-servolo-2018.png',
      category: 'training',
      title: 'ILAE Fellowship',
      location: 'San Servolo, Italy',
      year: '2018',
      description: 'Pediatric Epilepsy advanced training',
    },
    {
      id: 9,
      src: '/images/training/aiims-delhi-2015.png',
      category: 'training',
      title: 'AIIMS New Delhi',
      location: 'New Delhi, India',
      year: '2015',
      description: 'D.M. in Pediatric Neurology',
    },
    {
      id: 10,
      src: '/images/dignitaries/medical-board-meeting.png',
      category: 'dignitaries',
      title: 'Medical Board Meeting',
      location: 'India',
      year: '2023',
      description: 'With senior healthcare professionals and officials',
    },
    {
      id: 11,
      src: '/images/gallery/child-consultation.png',
      category: 'all',
      title: 'Patient Consultation',
      location: 'Indore, India',
      year: '2024',
      description: 'Compassionate care for young patients',
    },
    {
      id: 12,
      src: '/images/about/clinic-office-setting.png',
      category: 'all',
      title: 'Clinic Office',
      location: 'Medanta, Indore',
      year: '2024',
      description: 'Modern consultation space',
    },
  ];

  $effect(() => {
    if (lightboxOpen) {
      document.body.style.overflow = 'hidden';
    } else {
      document.body.style.overflow = '';
    }
  });

  function getFilteredItems() {
    if (selectedCategory === 'all') return galleryItems;
    return galleryItems.filter(item => item.category === selectedCategory);
  }

  function openLightbox(index: number) {
    lightboxIndex = index;
    lightboxOpen = true;
  }

  function closeLightbox() {
    lightboxOpen = false;
  }

  function nextImage() {
    const items = getFilteredItems();
    lightboxIndex = (lightboxIndex + 1) % items.length;
  }

  function prevImage() {
    const items = getFilteredItems();
    lightboxIndex = (lightboxIndex - 1 + items.length) % items.length;
  }

  function handleKeydown(e: KeyboardEvent) {
    if (!lightboxOpen) return;
    if (e.key === 'Escape') closeLightbox();
    if (e.key === 'ArrowRight') nextImage();
    if (e.key === 'ArrowLeft') prevImage();
  }
</script>

<svelte:window onkeydown={handleKeydown} />

<section id="gallery" class="gallery section">
  <div class="container">
    <div class="section-header">
      <p class="section-preheading">Moments of Care</p>
      <h2>A journey spanning <span class="highlight">25+ years</span> and 4 continents</h2>
    </div>

    <!-- Category filters -->
    <div class="category-filters">
      {#each categories as cat}
        <button
          class="filter-btn"
          class:active={selectedCategory === cat.id}
          onclick={() => selectedCategory = cat.id}
        >
          {cat.label}
        </button>
      {/each}
    </div>

    <!-- Gallery grid -->
    <div class="gallery-grid">
      {#each getFilteredItems() as item, i}
        <button
          class="gallery-item"
          onclick={() => openLightbox(i)}
          aria-label="View {item.title}"
        >
          <img src={item.src} alt={item.title} loading="lazy" />
          <div class="item-overlay">
            <h4 class="item-title">{item.title}</h4>
            <p class="item-location">{item.location} • {item.year}</p>
          </div>
        </button>
      {/each}
    </div>
  </div>

  <!-- Lightbox -->
  {#if lightboxOpen}
    {@const items = getFilteredItems()}
    {@const currentItem = items[lightboxIndex]}
    <!-- svelte-ignore a11y_click_events_have_key_events a11y_interactive_supports_focus -->
    <div class="lightbox" onclick={closeLightbox} role="dialog" aria-modal="true" tabindex="-1">
      <button class="lightbox-close" onclick={closeLightbox} aria-label="Close">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <line x1="18" y1="6" x2="6" y2="18"/>
          <line x1="6" y1="6" x2="18" y2="18"/>
        </svg>
      </button>

      <button class="lightbox-nav prev" onclick={(e) => { e.stopPropagation(); prevImage(); }} aria-label="Previous">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <polyline points="15 18 9 12 15 6"/>
        </svg>
      </button>

      <!-- svelte-ignore a11y_click_events_have_key_events -->
      <div class="lightbox-content" role="presentation" onclick={(e) => e.stopPropagation()}>
        <img src={currentItem.src} alt={currentItem.title} />
        <div class="lightbox-info">
          <h3>{currentItem.title}</h3>
          <p class="lightbox-meta">{currentItem.location} • {currentItem.year}</p>
          <p class="lightbox-desc">{currentItem.description}</p>
        </div>
      </div>

      <button class="lightbox-nav next" onclick={(e) => { e.stopPropagation(); nextImage(); }} aria-label="Next">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <polyline points="9 18 15 12 9 6"/>
        </svg>
      </button>

      <div class="lightbox-counter">
        {lightboxIndex + 1} / {items.length}
      </div>
    </div>
  {/if}
</section>

<style>
  .gallery {
    background: var(--warm-white);
  }

  .section-header {
    text-align: center;
    margin-bottom: var(--space-xl);
  }

  .section-preheading {
    font-family: var(--font-accent);
    font-size: var(--text-xl);
    color: var(--color-primary);
    margin-bottom: var(--space-sm);
  }

  .section-header h2 {
    font-size: var(--text-3xl);
    line-height: 1.2;
  }

  .section-header .highlight {
    color: var(--color-secondary);
    font-style: italic;
  }

  /* Category filters */
  .category-filters {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: var(--space-sm);
    margin-bottom: var(--space-xl);
  }

  .filter-btn {
    padding: var(--space-sm) var(--space-lg);
    border: 1px solid var(--border-light);
    border-radius: var(--radius-full);
    background: var(--surface-primary);
    color: var(--text-secondary);
    font-size: var(--text-sm);
    cursor: pointer;
    transition: all var(--transition-fast);
  }

  .filter-btn:hover {
    border-color: var(--color-primary);
    color: var(--color-primary);
  }

  .filter-btn.active {
    background: var(--color-primary);
    border-color: var(--color-primary);
    color: white;
  }

  /* Gallery grid */
  .gallery-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: var(--space-md);
  }

  @media (min-width: 640px) {
    .gallery-grid {
      grid-template-columns: repeat(3, 1fr);
    }
  }

  @media (min-width: 1024px) {
    .gallery-grid {
      grid-template-columns: repeat(4, 1fr);
    }
  }

  .gallery-item {
    position: relative;
    aspect-ratio: 1;
    border-radius: var(--radius-md);
    overflow: hidden;
    cursor: pointer;
    border: none;
    padding: 0;
    background: none;
  }

  .gallery-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.4s ease;
  }

  .gallery-item:hover img {
    transform: scale(1.08);
  }

  .item-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to top, rgba(0,0,0,0.7) 0%, transparent 60%);
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    padding: var(--space-md);
    opacity: 0;
    transition: opacity 0.3s ease;
  }

  .gallery-item:hover .item-overlay,
  .gallery-item:focus .item-overlay {
    opacity: 1;
  }

  .item-title {
    color: white;
    font-size: var(--text-sm);
    font-weight: 600;
    margin-bottom: 4px;
  }

  .item-location {
    color: rgba(255,255,255,0.8);
    font-size: var(--text-xs);
  }

  /* Lightbox */
  .lightbox {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.95);
    z-index: 1000;
    display: flex;
    align-items: center;
    justify-content: center;
    animation: fade-in 0.3s ease;
  }

  @keyframes fade-in {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  .lightbox-close {
    position: absolute;
    top: var(--space-lg);
    right: var(--space-lg);
    width: 44px;
    height: 44px;
    border: none;
    background: rgba(255,255,255,0.1);
    border-radius: var(--radius-full);
    color: white;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background 0.2s;
    z-index: 10;
  }

  .lightbox-close:hover {
    background: rgba(255,255,255,0.2);
  }

  .lightbox-close svg {
    width: 24px;
    height: 24px;
  }

  .lightbox-nav {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    width: 50px;
    height: 50px;
    border: none;
    background: rgba(255,255,255,0.1);
    border-radius: var(--radius-full);
    color: white;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: background 0.2s;
    z-index: 10;
  }

  .lightbox-nav:hover {
    background: rgba(255,255,255,0.2);
  }

  .lightbox-nav svg {
    width: 28px;
    height: 28px;
  }

  .lightbox-nav.prev {
    left: var(--space-lg);
  }

  .lightbox-nav.next {
    right: var(--space-lg);
  }

  .lightbox-content {
    max-width: 80vw;
    max-height: 80vh;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .lightbox-content img {
    max-width: 100%;
    max-height: 65vh;
    object-fit: contain;
    border-radius: var(--radius-md);
  }

  .lightbox-info {
    text-align: center;
    color: white;
    margin-top: var(--space-lg);
    max-width: 500px;
  }

  .lightbox-info h3 {
    font-size: var(--text-xl);
    margin-bottom: var(--space-xs);
  }

  .lightbox-meta {
    color: var(--color-accent);
    font-size: var(--text-sm);
    margin-bottom: var(--space-sm);
  }

  .lightbox-desc {
    color: rgba(255,255,255,0.7);
    font-size: var(--text-sm);
  }

  .lightbox-counter {
    position: absolute;
    bottom: var(--space-lg);
    left: 50%;
    transform: translateX(-50%);
    color: rgba(255,255,255,0.6);
    font-size: var(--text-sm);
  }

  @media (max-width: 640px) {
    .lightbox-nav {
      width: 40px;
      height: 40px;
    }

    .lightbox-nav.prev {
      left: var(--space-sm);
    }

    .lightbox-nav.next {
      right: var(--space-sm);
    }

    .lightbox-content {
      max-width: 95vw;
    }
  }
</style>
