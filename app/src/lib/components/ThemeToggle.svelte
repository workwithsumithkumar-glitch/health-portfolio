<script lang="ts">
  import { onMount } from 'svelte';

  let theme = $state<'light' | 'dark' | 'system'>('system');
  let resolvedTheme = $state<'light' | 'dark'>('light');

  onMount(() => {
    // Check for saved preference
    const saved = localStorage.getItem('theme') as 'light' | 'dark' | 'system' | null;
    if (saved) {
      theme = saved;
    }

    // Apply theme
    applyTheme();

    // Listen for system preference changes
    const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)');
    mediaQuery.addEventListener('change', handleSystemChange);

    return () => {
      mediaQuery.removeEventListener('change', handleSystemChange);
    };
  });

  function handleSystemChange() {
    if (theme === 'system') {
      applyTheme();
    }
  }

  function applyTheme() {
    const systemDark = window.matchMedia('(prefers-color-scheme: dark)').matches;

    if (theme === 'system') {
      resolvedTheme = systemDark ? 'dark' : 'light';
      document.documentElement.removeAttribute('data-theme');
    } else {
      resolvedTheme = theme;
      document.documentElement.setAttribute('data-theme', theme);
    }
  }

  function toggleTheme() {
    // Cycle through: system -> light -> dark -> system
    if (theme === 'system') {
      theme = 'light';
    } else if (theme === 'light') {
      theme = 'dark';
    } else {
      theme = 'system';
    }

    localStorage.setItem('theme', theme);
    applyTheme();
  }
</script>

<button
  class="theme-toggle"
  onclick={toggleTheme}
  type="button"
  aria-label="Toggle theme (current: {theme})"
  title="Theme: {theme}"
>
  {#if theme === 'system'}
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="icon-system">
      <rect x="2" y="3" width="20" height="14" rx="2" ry="2"/>
      <line x1="8" y1="21" x2="16" y2="21"/>
      <line x1="12" y1="17" x2="12" y2="21"/>
    </svg>
  {:else if resolvedTheme === 'light'}
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="icon-light">
      <circle cx="12" cy="12" r="5"/>
      <line x1="12" y1="1" x2="12" y2="3"/>
      <line x1="12" y1="21" x2="12" y2="23"/>
      <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/>
      <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/>
      <line x1="1" y1="12" x2="3" y2="12"/>
      <line x1="21" y1="12" x2="23" y2="12"/>
      <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/>
      <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/>
    </svg>
  {:else}
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="icon-dark">
      <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>
    </svg>
  {/if}
</button>

<style>
  .theme-toggle {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
    padding: 8px;
    background: transparent;
    border: 2px solid var(--border-light);
    border-radius: var(--radius-full);
    color: var(--text-primary);
    cursor: pointer;
    transition: all var(--transition-fast);
  }

  .theme-toggle:hover {
    background: var(--surface-secondary);
    border-color: var(--color-primary);
    color: var(--color-primary);
  }

  .theme-toggle svg {
    width: 20px;
    height: 20px;
  }

  .icon-light {
    color: var(--warning);
  }

  .icon-dark {
    color: var(--color-tertiary);
  }

  .icon-system {
    color: var(--text-secondary);
  }
</style>
