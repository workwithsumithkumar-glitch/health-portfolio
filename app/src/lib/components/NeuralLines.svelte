<script lang="ts">
  import { onMount } from 'svelte';

  let visible = $state(false);

  onMount(() => {
    visible = true;
  });
</script>

<div class="neural-lines" class:visible aria-hidden="true">
  <svg viewBox="0 0 1200 800" preserveAspectRatio="none" fill="none" xmlns="http://www.w3.org/2000/svg">
    <!-- Flowing neural pathways -->
    <path
      class="neural-path path-1"
      d="M-50 200 Q200 150 400 300 T800 250 T1250 400"
      stroke="url(#gradient1)"
      stroke-width="2"
      fill="none"
    />
    <path
      class="neural-path path-2"
      d="M-50 500 Q150 450 350 550 T700 480 T1250 600"
      stroke="url(#gradient2)"
      stroke-width="1.5"
      fill="none"
    />
    <path
      class="neural-path path-3"
      d="M1250 100 Q1000 200 800 150 T400 250 T-50 180"
      stroke="url(#gradient3)"
      stroke-width="2"
      fill="none"
    />
    <path
      class="neural-path path-4"
      d="M600 -50 Q550 150 650 300 T580 500 T620 850"
      stroke="url(#gradient1)"
      stroke-width="1.5"
      fill="none"
    />

    <!-- Synapse nodes -->
    <circle class="synapse s1" cx="400" cy="300" r="4" fill="var(--color-accent)"/>
    <circle class="synapse s2" cx="800" cy="250" r="3" fill="var(--color-soft)"/>
    <circle class="synapse s3" cx="350" cy="550" r="5" fill="var(--color-tertiary)"/>
    <circle class="synapse s4" cx="700" cy="480" r="3" fill="var(--color-light)"/>
    <circle class="synapse s5" cx="650" cy="300" r="4" fill="var(--color-secondary)"/>

    <!-- Gradients -->
    <defs>
      <linearGradient id="gradient1" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" stop-color="var(--color-accent)" stop-opacity="0.1"/>
        <stop offset="50%" stop-color="var(--color-primary)" stop-opacity="0.2"/>
        <stop offset="100%" stop-color="var(--color-secondary)" stop-opacity="0.1"/>
      </linearGradient>
      <linearGradient id="gradient2" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" stop-color="var(--color-soft)" stop-opacity="0.1"/>
        <stop offset="50%" stop-color="var(--color-tertiary)" stop-opacity="0.15"/>
        <stop offset="100%" stop-color="var(--color-light)" stop-opacity="0.1"/>
      </linearGradient>
      <linearGradient id="gradient3" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" stop-color="var(--color-secondary)" stop-opacity="0.1"/>
        <stop offset="50%" stop-color="var(--color-accent)" stop-opacity="0.15"/>
        <stop offset="100%" stop-color="var(--color-primary)" stop-opacity="0.1"/>
      </linearGradient>
    </defs>
  </svg>
</div>

<style>
  .neural-lines {
    position: absolute;
    inset: 0;
    overflow: hidden;
    pointer-events: none;
    z-index: 0;
    opacity: 0;
    transition: opacity 1s ease-out;
  }

  .neural-lines.visible {
    opacity: 1;
  }

  .neural-lines svg {
    width: 100%;
    height: 100%;
  }

  .neural-path {
    stroke-dasharray: 1500;
    stroke-dashoffset: 1500;
    animation: draw-path 3s ease-out forwards;
  }

  .path-1 { animation-delay: 0.2s; }
  .path-2 { animation-delay: 0.5s; }
  .path-3 { animation-delay: 0.8s; }
  .path-4 { animation-delay: 1.1s; }

  @keyframes draw-path {
    to {
      stroke-dashoffset: 0;
    }
  }

  .synapse {
    opacity: 0;
    animation: pulse-in 0.5s ease-out forwards;
  }

  .s1 { animation-delay: 1.5s; }
  .s2 { animation-delay: 1.7s; }
  .s3 { animation-delay: 1.9s; }
  .s4 { animation-delay: 2.1s; }
  .s5 { animation-delay: 2.3s; }

  @keyframes pulse-in {
    0% {
      opacity: 0;
      transform: scale(0);
    }
    50% {
      opacity: 0.6;
      transform: scale(1.5);
    }
    100% {
      opacity: 0.4;
      transform: scale(1);
    }
  }

  @media (prefers-reduced-motion: reduce) {
    .neural-path {
      animation: none;
      stroke-dashoffset: 0;
    }

    .synapse {
      animation: none;
      opacity: 0.4;
    }
  }
</style>
