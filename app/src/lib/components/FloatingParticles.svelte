<script lang="ts">
  const particles = [
    { size: 12, x: 10, y: 20, delay: 0, duration: 25, color: 'var(--color-light)' },
    { size: 8, x: 85, y: 15, delay: 5, duration: 30, color: 'var(--color-soft)' },
    { size: 15, x: 75, y: 70, delay: 2, duration: 28, color: 'var(--color-accent)' },
    { size: 6, x: 20, y: 75, delay: 8, duration: 22, color: 'var(--color-tertiary)' },
    { size: 10, x: 50, y: 85, delay: 4, duration: 26, color: 'var(--color-light)' },
    { size: 18, x: 90, y: 45, delay: 6, duration: 32, color: 'var(--color-soft)' },
    { size: 7, x: 30, y: 40, delay: 3, duration: 24, color: 'var(--color-accent)' },
    { size: 14, x: 65, y: 30, delay: 7, duration: 27, color: 'var(--color-tertiary)' },
  ];
</script>

<div class="particles" aria-hidden="true">
  {#each particles as particle, i}
    <div
      class="particle"
      style="
        width: {particle.size}px;
        height: {particle.size}px;
        left: {particle.x}%;
        top: {particle.y}%;
        background: {particle.color};
        animation-delay: {particle.delay}s;
        animation-duration: {particle.duration}s;
      "
    ></div>
  {/each}
</div>

<style>
  .particles {
    position: absolute;
    inset: 0;
    overflow: hidden;
    pointer-events: none;
    z-index: 1;
  }

  .particle {
    position: absolute;
    border-radius: 50%;
    opacity: 0.3;
    animation: drift linear infinite;
  }

  @keyframes drift {
    0% {
      transform: translate(0, 0) scale(1);
      opacity: 0.3;
    }
    25% {
      transform: translate(20px, -30px) scale(1.1);
      opacity: 0.4;
    }
    50% {
      transform: translate(-10px, -50px) scale(0.9);
      opacity: 0.2;
    }
    75% {
      transform: translate(30px, -20px) scale(1.05);
      opacity: 0.35;
    }
    100% {
      transform: translate(0, 0) scale(1);
      opacity: 0.3;
    }
  }

  @media (prefers-reduced-motion: reduce) {
    .particle {
      animation: none;
    }
  }
</style>
