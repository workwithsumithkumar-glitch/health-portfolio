<script lang="ts">
  import { onMount } from 'svelte';
  import ThemeToggle from './ThemeToggle.svelte';

  let scrolled = $state(false);
  let mobileMenuOpen = $state(false);

  const navLinks = [
    { href: '#home', label: 'Home' },
    { href: '#about', label: 'About' },
    { href: '#expertise', label: 'Expertise' },
    { href: '#gallery', label: 'Gallery' },
    { href: '#research', label: 'Research' },
    { href: '#contact', label: 'Contact' },
  ];

  onMount(() => {
    const handleScroll = () => {
      scrolled = window.scrollY > 50;
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  });

  function toggleMenu() {
    mobileMenuOpen = !mobileMenuOpen;
  }

  function closeMenu() {
    mobileMenuOpen = false;
  }
</script>

<nav class="nav" class:scrolled>
  <div class="nav-container">
    <a href="#home" class="logo" onclick={closeMenu}>
      <span class="logo-icon">
        <svg viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="20" cy="20" r="18" stroke="currentColor" stroke-width="2"/>
          <path d="M20 8 C25 12, 28 16, 20 24 C12 16, 15 12, 20 8" fill="currentColor" opacity="0.3"/>
          <circle cx="20" cy="16" r="3" fill="currentColor"/>
          <path d="M14 22 Q20 28 26 22" stroke="currentColor" stroke-width="2" fill="none"/>
        </svg>
      </span>
      <span class="logo-text">Dr. Rachana Dubey</span>
    </a>

    <button class="mobile-toggle" onclick={toggleMenu} aria-label="Toggle menu" aria-expanded={mobileMenuOpen}>
      <span class="hamburger" class:open={mobileMenuOpen}>
        <span></span>
        <span></span>
        <span></span>
      </span>
    </button>

    <div class="nav-links" class:open={mobileMenuOpen}>
      {#each navLinks as link}
        <a href={link.href} class="nav-link" onclick={closeMenu}>{link.label}</a>
      {/each}
      <ThemeToggle />
      <a href="#contact" class="nav-cta" onclick={closeMenu}>Book Consultation</a>
    </div>
  </div>
</nav>

{#if mobileMenuOpen}
  <button class="mobile-overlay" onclick={closeMenu} type="button" aria-label="Close menu"></button>
{/if}

<style>
  .nav {
    position: fixed;
    top: var(--space-md);
    left: 50%;
    transform: translateX(-50%);
    width: calc(100% - var(--space-lg));
    max-width: 1000px;
    z-index: 1000;
    background: color-mix(in srgb, var(--warm-white) 85%, transparent);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border-radius: var(--radius-full);
    box-shadow: var(--shadow-md);
    transition: all var(--transition-base);
    border: 1px solid var(--border-light);
  }

  .nav.scrolled {
    top: var(--space-sm);
    background: color-mix(in srgb, var(--warm-white) 95%, transparent);
    box-shadow: var(--shadow-lg);
  }

  .nav-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: var(--space-sm) var(--space-md);
  }

  .logo {
    display: flex;
    align-items: center;
    gap: var(--space-sm);
    color: var(--color-primary);
    font-family: var(--font-display);
    font-weight: 600;
    font-size: var(--text-lg);
    text-decoration: none;
  }

  .logo-icon {
    width: 40px;
    height: 40px;
    color: var(--color-primary);
  }

  .logo-icon svg {
    width: 100%;
    height: 100%;
  }

  .logo-text {
    display: none;
  }

  @media (min-width: 768px) {
    .logo-text {
      display: inline;
    }
  }

  .nav-links {
    display: none;
    align-items: center;
    gap: var(--space-md);
  }

  @media (min-width: 768px) {
    .nav-links {
      display: flex;
    }
  }

  .nav-link {
    color: var(--text-primary);
    font-weight: 500;
    font-size: var(--text-sm);
    text-decoration: none;
    padding: var(--space-xs) var(--space-sm);
    border-radius: var(--radius-sm);
    transition: all var(--transition-fast);
    position: relative;
  }

  .nav-link::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 50%;
    width: 0;
    height: 2px;
    background: var(--color-secondary);
    transition: all var(--transition-fast);
    transform: translateX(-50%);
  }

  .nav-link:hover::after {
    width: 100%;
  }

  .nav-link:hover {
    color: var(--color-secondary);
  }

  .nav-cta {
    background: var(--gradient-hope);
    color: var(--deep-charcoal);
    padding: var(--space-sm) var(--space-md);
    border-radius: var(--radius-full);
    font-weight: 600;
    font-size: var(--text-sm);
    text-decoration: none;
    transition: all var(--transition-base);
  }

  .nav-cta:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(232, 80, 154, 0.3);
  }

  /* Mobile Menu Toggle */
  .mobile-toggle {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 44px;
    height: 44px;
    background: transparent;
    border: none;
    cursor: pointer;
    z-index: 1001;
  }

  @media (min-width: 768px) {
    .mobile-toggle {
      display: none;
    }
  }

  .hamburger {
    display: flex;
    flex-direction: column;
    gap: 5px;
    width: 24px;
  }

  .hamburger span {
    display: block;
    height: 2px;
    background: var(--text-primary);
    border-radius: 2px;
    transition: all var(--transition-base);
  }

  .hamburger.open span:nth-child(1) {
    transform: rotate(45deg) translate(5px, 5px);
  }

  .hamburger.open span:nth-child(2) {
    opacity: 0;
  }

  .hamburger.open span:nth-child(3) {
    transform: rotate(-45deg) translate(5px, -5px);
  }

  /* Mobile Menu */
  @media (max-width: 767px) {
    .nav-links {
      position: fixed;
      top: 0;
      right: -100%;
      width: 80%;
      max-width: 320px;
      height: 100vh;
      background: var(--surface-primary);
      flex-direction: column;
      align-items: flex-start;
      padding: var(--space-2xl) var(--space-lg);
      gap: var(--space-lg);
      transition: right var(--transition-base);
      box-shadow: var(--shadow-lg);
      border-left: 1px solid var(--border-light);
    }

    .nav-links.open {
      display: flex;
      right: 0;
    }

    .nav-link {
      font-size: var(--text-lg);
    }

    .nav-cta {
      margin-top: var(--space-md);
      padding: var(--space-md) var(--space-lg);
    }
  }

  .mobile-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(45, 42, 62, 0.5);
    z-index: 999;
    border: none;
    cursor: pointer;
  }

  @media (max-width: 767px) {
    .mobile-overlay {
      display: block;
    }
  }
</style>
