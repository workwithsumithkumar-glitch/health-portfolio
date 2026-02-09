<script lang="ts">
  import { onMount } from 'svelte';

  let isVisible = $state(false);

  onMount(() => {
    const handleScroll = () => {
      isVisible = window.scrollY > 300;
    };

    window.addEventListener('scroll', handleScroll, { passive: true });
    handleScroll(); // Check initial position

    return () => {
      window.removeEventListener('scroll', handleScroll);
    };
  });

  function scrollToTop() {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }
</script>

<button
  class="back-to-top"
  class:visible={isVisible}
  onclick={scrollToTop}
  type="button"
  aria-label="Back to top"
  title="Back to top"
>
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
    <polyline points="18 15 12 9 6 15"/>
  </svg>
</button>

<style>
  .back-to-top {
    position: fixed;
    bottom: 2rem;
    right: 2rem;
    z-index: 900;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 48px;
    height: 48px;
    padding: 0;
    background: var(--gradient-hope);
    border: none;
    border-radius: var(--radius-full);
    color: white;
    cursor: pointer;
    box-shadow: var(--shadow-lg);
    opacity: 0;
    visibility: hidden;
    transform: translateY(20px) scale(0.8);
    transition: all var(--transition-base);
  }

  .back-to-top.visible {
    opacity: 1;
    visibility: visible;
    transform: translateY(0) scale(1);
  }

  .back-to-top:hover {
    transform: translateY(-4px) scale(1.05);
    box-shadow: var(--shadow-xl, 0 25px 50px -12px rgba(0, 0, 0, 0.25));
  }

  .back-to-top:active {
    transform: translateY(0) scale(0.95);
  }

  .back-to-top svg {
    width: 24px;
    height: 24px;
  }

  @media (max-width: 768px) {
    .back-to-top {
      bottom: 1.5rem;
      right: 1.5rem;
      width: 44px;
      height: 44px;
    }

    .back-to-top svg {
      width: 20px;
      height: 20px;
    }
  }

  @media (prefers-reduced-motion: reduce) {
    .back-to-top {
      transition: opacity var(--transition-fast), visibility var(--transition-fast);
    }

    .back-to-top.visible {
      transform: none;
    }

    .back-to-top:hover {
      transform: none;
    }
  }
</style>
