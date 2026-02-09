<script lang="ts">
  let selectedThumb = $state(0);

  const galleryImages = [
    { src: '/images/about/clinic-office-setting.png', alt: 'Dr. Dubey in her clinic' },
    { src: '/images/gallery/child-consultation.png', alt: 'Consultation with a young patient' },
    { src: '/images/conferences/world-neurology-congress-2023.png', alt: 'Speaking at World Neurology Congress' },
  ];
</script>

<section id="about" class="story section">
  <div class="container">
    <div class="story-grid">
      <div class="story-image">
        <div class="image-frame">
          <img
            src={galleryImages[selectedThumb].src}
            alt={galleryImages[selectedThumb].alt}
            class="story-photo"
            loading="lazy"
          />
        </div>
        <div class="image-accent"></div>
        <div class="floating-badge">
          <span class="badge-number">25+</span>
          <span class="badge-text">Years of Care</span>
        </div>

        <!-- Mini gallery thumbnails -->
        <div class="story-gallery">
          {#each galleryImages as img, i}
            <button
              class="gallery-thumb"
              class:active={selectedThumb === i}
              onclick={() => selectedThumb = i}
              aria-label="View {img.alt}"
            >
              <img src={img.src} alt={img.alt} loading="lazy" />
            </button>
          {/each}
        </div>
      </div>

      <div class="story-content">
        <p class="story-preheading">The Journey</p>
        <h2 class="story-heading">A journey of<br/><span class="highlight">understanding</span></h2>

        <blockquote class="story-quote">
          "Every brain has potential waiting to bloom."
        </blockquote>

        <div class="story-text">
          <p>
            From the halls of AIIMS Delhi to the Cleveland Clinic, from Paris to Cambridge — my path has always led back to one place: <strong>a child's bedside</strong>.
          </p>
          <p>
            I began my journey in Bhopal, driven by a simple question: How can we help children whose minds work differently? That question took me across four countries, through countless research papers, and into the lives of thousands of families.
          </p>
          <p>
            After training at the world's leading institutions, I chose to return to Central India. Because excellence in neurology shouldn't require a passport. Every child in Indore deserves the same care available in Cleveland or Cambridge.
          </p>
          <p>
            25 years later, I'm still learning. Still caring. Still believing that understanding is the first step to healing.
          </p>
        </div>

        <a href="#contact" class="btn btn-secondary">
          Start a Conversation
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
            <path d="M6 12L10 8L6 4" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </a>
      </div>
    </div>
  </div>
</section>

<style>
  .story {
    background: var(--warm-white);
    overflow: hidden;
  }

  .story-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: var(--space-xl);
    align-items: center;
  }

  @media (min-width: 768px) {
    .story-grid {
      grid-template-columns: 1fr 1.2fr;
      gap: var(--space-2xl);
    }
  }

  .story-image {
    position: relative;
    display: flex;
    justify-content: center;
  }

  .image-frame {
    position: relative;
    width: 280px;
    height: 360px;
    border-radius: var(--radius-xl);
    overflow: hidden;
    box-shadow: var(--shadow-lg);
    background: var(--surface-primary);
    border: 1px solid var(--border-light);
  }

  @media (min-width: 768px) {
    .image-frame {
      width: 320px;
      height: 420px;
    }
  }

  .story-photo {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.5s ease;
  }

  .image-frame:hover .story-photo {
    transform: scale(1.03);
  }

  .story-gallery {
    display: flex;
    gap: var(--space-sm);
    margin-top: var(--space-md);
    justify-content: center;
  }

  .gallery-thumb {
    width: 60px;
    height: 60px;
    border-radius: var(--radius-md);
    overflow: hidden;
    border: 2px solid transparent;
    cursor: pointer;
    transition: all var(--transition-fast);
    padding: 0;
    background: none;
    opacity: 0.6;
  }

  .gallery-thumb:hover {
    opacity: 0.9;
  }

  .gallery-thumb.active {
    border-color: var(--color-secondary);
    opacity: 1;
    box-shadow: var(--shadow-md);
  }

  .gallery-thumb img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  @media (min-width: 768px) {
    .gallery-thumb {
      width: 70px;
      height: 70px;
    }
  }

  .image-accent {
    position: absolute;
    width: 200px;
    height: 200px;
    background: var(--gradient-trust);
    border-radius: 50%;
    bottom: -60px;
    left: -60px;
    opacity: 0.3;
    z-index: -1;
  }

  .floating-badge {
    position: absolute;
    bottom: 40px;
    right: -20px;
    background: var(--surface-primary);
    padding: var(--space-md) var(--space-lg);
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow-lg);
    text-align: center;
    animation: float 4s ease-in-out infinite;
    border: 1px solid var(--border-light);
  }

  @media (min-width: 768px) {
    .floating-badge {
      right: -40px;
    }
  }

  .badge-number {
    display: block;
    font-family: var(--font-display);
    font-size: var(--text-2xl);
    font-weight: 600;
    color: var(--color-secondary);
    line-height: 1;
  }

  .badge-text {
    font-size: var(--text-sm);
    color: var(--text-muted);
  }

  .story-content {
    padding: var(--space-md) 0;
  }

  .story-preheading {
    font-family: var(--font-accent);
    font-size: var(--text-xl);
    color: var(--color-primary);
    margin-bottom: var(--space-sm);
  }

  .story-heading {
    font-size: var(--text-4xl);
    margin-bottom: var(--space-lg);
    line-height: 1.1;
  }

  .story-heading .highlight {
    color: var(--color-secondary);
    font-style: italic;
  }

  .story-quote {
    font-family: var(--font-accent);
    font-size: var(--text-2xl);
    color: var(--color-primary);
    border-left: 4px solid var(--color-secondary);
    padding-left: var(--space-md);
    margin: var(--space-lg) 0;
    font-style: italic;
  }

  .story-text {
    margin-bottom: var(--space-lg);
  }

  .story-text p {
    margin-bottom: var(--space-md);
    color: var(--text-primary);
    line-height: 1.8;
  }

  .story-text strong {
    color: var(--color-primary);
  }
</style>
