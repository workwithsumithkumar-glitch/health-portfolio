<script lang="ts">
  import { onMount, onDestroy } from 'svelte';

  const testimonials = [
    {
      id: 1,
      quote: "Dr. Dubey didn't just treat my son's epilepsy. She treated our family's fear. After two years of uncertainty, we finally found hope.",
      author: 'Priya M.',
      relation: 'Mother of Arjun (8)',
    },
    {
      id: 2,
      quote: "The way she explains complex medical conditions in simple terms gave us clarity we never had before. Our daughter is thriving now.",
      author: 'Rajesh K.',
      relation: 'Father of Ananya (6)',
    },
    {
      id: 3,
      quote: "She took time to understand our child as a person, not just a patient. That made all the difference in his treatment journey.",
      author: 'Meera S.',
      relation: 'Mother of Vivaan (10)',
    },
    {
      id: 4,
      quote: "When every other doctor gave up, Dr. Dubey's persistence and expertise led to a correct diagnosis. We are forever grateful.",
      author: 'Amit P.',
      relation: 'Father of Riya (5)',
    },
  ];

  let currentIndex = $state(0);
  let intervalId: number;

  function nextTestimonial() {
    currentIndex = (currentIndex + 1) % testimonials.length;
  }

  function prevTestimonial() {
    currentIndex = (currentIndex - 1 + testimonials.length) % testimonials.length;
  }

  function goToTestimonial(index: number) {
    currentIndex = index;
  }

  onMount(() => {
    intervalId = setInterval(nextTestimonial, 6000);
  });

  onDestroy(() => {
    if (intervalId) clearInterval(intervalId);
  });
</script>

<section class="testimonials section">
  <div class="container">
    <div class="section-header">
      <h2>Stories from Families</h2>
      <p class="section-subtitle">The journey of healing, told by those who walked it.</p>
    </div>

    <div class="testimonial-carousel">
      <button class="carousel-btn prev" onclick={prevTestimonial} aria-label="Previous testimonial">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
          <path d="M15 18L9 12L15 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>

      <div class="testimonial-content">
        <div class="quote-mark" aria-hidden="true">"</div>

        <div class="testimonials-track" style="transform: translateX(-{currentIndex * 100}%)">
          {#each testimonials as testimonial}
            <div class="testimonial-slide">
              <blockquote class="testimonial-quote">
                {testimonial.quote}
              </blockquote>
              <div class="testimonial-author">
                <div class="author-avatar">
                  <svg viewBox="0 0 40 40" fill="none">
                    <circle cx="20" cy="20" r="20" fill="var(--color-light)"/>
                    <circle cx="20" cy="16" r="8" fill="var(--color-primary)" opacity="0.3"/>
                    <path d="M8 36 Q20 28 32 36" fill="var(--color-primary)" opacity="0.3"/>
                  </svg>
                </div>
                <div class="author-info">
                  <span class="author-name">{testimonial.author}</span>
                  <span class="author-relation">{testimonial.relation}</span>
                </div>
              </div>
            </div>
          {/each}
        </div>
      </div>

      <button class="carousel-btn next" onclick={nextTestimonial} aria-label="Next testimonial">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
          <path d="M9 18L15 12L9 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>
    </div>

    <div class="carousel-dots">
      {#each testimonials as _, i}
        <button
          class="dot"
          class:active={i === currentIndex}
          onclick={() => goToTestimonial(i)}
          aria-label="Go to testimonial {i + 1}"
        ></button>
      {/each}
    </div>
  </div>
</section>

<style>
  .testimonials {
    background: linear-gradient(135deg, color-mix(in srgb, var(--color-light) 20%, var(--warm-white)) 0%, var(--surface-secondary) 100%);
    overflow: hidden;
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
  }

  .testimonial-carousel {
    display: flex;
    align-items: center;
    gap: var(--space-md);
    max-width: 900px;
    margin: 0 auto;
  }

  .carousel-btn {
    flex-shrink: 0;
    width: 48px;
    height: 48px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: var(--surface-primary);
    border: 1px solid var(--border-light);
    border-radius: 50%;
    color: var(--color-primary);
    cursor: pointer;
    box-shadow: var(--shadow-md);
    transition: all var(--transition-fast);
  }

  .carousel-btn:hover {
    background: var(--color-primary);
    color: var(--warm-white);
    transform: scale(1.1);
  }

  @media (max-width: 640px) {
    .carousel-btn {
      display: none;
    }
  }

  .testimonial-content {
    position: relative;
    flex: 1;
    overflow: hidden;
    background: var(--surface-primary);
    border-radius: var(--radius-xl);
    padding: var(--space-xl);
    box-shadow: var(--shadow-lg);
    border: 1px solid var(--border-light);
  }

  .quote-mark {
    position: absolute;
    top: var(--space-md);
    left: var(--space-lg);
    font-family: var(--font-display);
    font-size: 6rem;
    line-height: 1;
    color: var(--color-secondary);
    opacity: 0.2;
    pointer-events: none;
  }

  .testimonials-track {
    display: flex;
    transition: transform 0.5s ease-out;
  }

  .testimonial-slide {
    flex: 0 0 100%;
    min-width: 100%;
    padding: var(--space-md);
  }

  .testimonial-quote {
    font-family: var(--font-display);
    font-size: var(--text-xl);
    font-weight: 400;
    font-style: italic;
    color: var(--text-primary);
    line-height: 1.6;
    margin-bottom: var(--space-lg);
    text-align: center;
  }

  @media (min-width: 768px) {
    .testimonial-quote {
      font-size: var(--text-2xl);
    }
  }

  .testimonial-author {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: var(--space-md);
  }

  .author-avatar {
    width: 48px;
    height: 48px;
    border-radius: 50%;
    overflow: hidden;
  }

  .author-avatar svg {
    width: 100%;
    height: 100%;
  }

  .author-info {
    text-align: left;
  }

  .author-name {
    display: block;
    font-weight: 600;
    color: var(--text-primary);
  }

  .author-relation {
    display: block;
    font-size: var(--text-sm);
    color: var(--text-muted);
  }

  .carousel-dots {
    display: flex;
    justify-content: center;
    gap: var(--space-sm);
    margin-top: var(--space-lg);
  }

  .dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    border: none;
    background: var(--border-light);
    cursor: pointer;
    transition: all var(--transition-fast);
  }

  .dot.active {
    background: var(--color-secondary);
    transform: scale(1.2);
  }

  .dot:hover:not(.active) {
    background: var(--color-primary);
  }
</style>
