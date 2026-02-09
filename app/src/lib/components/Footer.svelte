<script lang="ts">
  const currentYear = new Date().getFullYear();

  const quickLinks = [
    { href: '#home', label: 'Home' },
    { href: '#about', label: 'About' },
    { href: '#research', label: 'Research' },
    { href: '#contact', label: 'Contact' },
  ];

  const expertiseLinks = [
    { href: '#epilepsy', label: 'Epilepsy' },
    { href: '#autism', label: 'Autism Spectrum' },
    { href: '#movement', label: 'Movement Disorders' },
    { href: '#developmental', label: 'Developmental Delays' },
  ];
</script>

<footer class="footer">
  <div class="footer-decoration" aria-hidden="true">
    <svg viewBox="0 0 1200 100" preserveAspectRatio="none">
      <path d="M0,50 Q300,0 600,50 T1200,50 L1200,100 L0,100 Z" fill="#1A1625"/>
    </svg>
  </div>

  <div class="footer-main">
    <div class="container">
      <div class="footer-grid">
        <div class="footer-brand">
          <a href="#home" class="footer-logo">
            <span class="logo-icon">
              <svg viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
                <circle cx="20" cy="20" r="18" stroke="currentColor" stroke-width="2"/>
                <path d="M20 8 C25 12, 28 16, 20 24 C12 16, 15 12, 20 8" fill="currentColor" opacity="0.3"/>
                <circle cx="20" cy="16" r="3" fill="currentColor"/>
                <path d="M14 22 Q20 28 26 22" stroke="currentColor" stroke-width="2" fill="none"/>
              </svg>
            </span>
            <div class="logo-text">
              <span class="logo-name">Dr. Rachana Dubey</span>
              <span class="logo-title">Pediatric Neurologist</span>
            </div>
          </a>
          <p class="footer-tagline">
            Every brain tells a story. We help write beautiful chapters.
          </p>
        </div>

        <div class="footer-links">
          <h4>Quick Links</h4>
          <ul>
            {#each quickLinks as link}
              <li><a href={link.href}>{link.label}</a></li>
            {/each}
          </ul>
        </div>

        <div class="footer-links">
          <h4>Expertise</h4>
          <ul>
            {#each expertiseLinks as link}
              <li><a href={link.href}>{link.label}</a></li>
            {/each}
          </ul>
        </div>

        <div class="footer-contact">
          <h4>Connect</h4>
          <ul>
            <li>
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/>
                <circle cx="12" cy="10" r="3"/>
              </svg>
              Medanta Hospital, Indore
            </li>
            <li>
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/>
              </svg>
              <a href="tel:+918839708182">+91 8839708182</a>
            </li>
            <li>
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
                <polyline points="22,6 12,13 2,6"/>
              </svg>
              <a href="mailto:rachnadube@gmail.com">rachnadube@gmail.com</a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>

  <div class="footer-bottom">
    <div class="container">
      <div class="footer-bottom-content">
        <p>&copy; {currentYear} Dr. Rachana Dubey. All rights reserved.</p>
        <div class="footer-legal">
          <a href="/privacy">Privacy Policy</a>
          <a href="/terms">Terms of Service</a>
        </div>
      </div>
    </div>
  </div>
</footer>

<style>
  .footer {
    position: relative;
    background: #1A1625;
    color: rgba(255, 255, 255, 0.8);
  }

  .footer-decoration {
    position: absolute;
    top: -50px;
    left: 0;
    right: 0;
    height: 100px;
    pointer-events: none;
  }

  .footer-decoration svg {
    width: 100%;
    height: 100%;
  }

  .footer-main {
    padding: var(--space-2xl) 0 var(--space-xl);
  }

  .footer-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: var(--space-xl);
  }

  @media (min-width: 640px) {
    .footer-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (min-width: 1024px) {
    .footer-grid {
      grid-template-columns: 2fr 1fr 1fr 1.5fr;
    }
  }

  .footer-brand {
    max-width: 300px;
  }

  .footer-logo {
    display: flex;
    align-items: center;
    gap: var(--space-sm);
    color: white;
    text-decoration: none;
    margin-bottom: var(--space-md);
  }

  .logo-icon {
    width: 48px;
    height: 48px;
    color: var(--color-light);
  }

  .logo-icon svg {
    width: 100%;
    height: 100%;
  }

  .logo-text {
    display: flex;
    flex-direction: column;
  }

  .logo-name {
    font-family: var(--font-display);
    font-size: var(--text-lg);
    font-weight: 600;
    color: white;
  }

  .logo-title {
    font-size: var(--text-sm);
    color: var(--color-light);
  }

  .footer-tagline {
    font-family: var(--font-body);
    font-size: var(--text-lg);
    color: rgba(255, 255, 255, 0.6);
  }

  .footer-links h4,
  .footer-contact h4 {
    font-family: var(--font-body);
    font-size: var(--text-sm);
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--color-light);
    margin-bottom: var(--space-md);
  }

  .footer-links ul,
  .footer-contact ul {
    list-style: none;
  }

  .footer-links li {
    margin-bottom: var(--space-sm);
  }

  .footer-links a {
    color: rgba(255, 255, 255, 0.7);
    text-decoration: none;
    transition: color var(--transition-fast);
  }

  .footer-links a:hover {
    color: var(--color-light);
  }

  .footer-contact li {
    display: flex;
    align-items: flex-start;
    gap: var(--space-sm);
    margin-bottom: var(--space-sm);
    font-size: var(--text-sm);
  }

  .footer-contact svg {
    width: 18px;
    height: 18px;
    flex-shrink: 0;
    color: var(--color-light);
    margin-top: 2px;
  }

  .footer-contact a {
    color: rgba(255, 255, 255, 0.7);
    text-decoration: none;
    transition: color var(--transition-fast);
  }

  .footer-contact a:hover {
    color: var(--color-light);
  }

  .footer-bottom {
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    padding: var(--space-md) 0;
  }

  .footer-bottom-content {
    display: flex;
    flex-direction: column;
    gap: var(--space-sm);
    align-items: center;
    text-align: center;
  }

  @media (min-width: 640px) {
    .footer-bottom-content {
      flex-direction: row;
      justify-content: space-between;
      text-align: left;
    }
  }

  .footer-bottom p {
    font-size: var(--text-sm);
    color: rgba(255, 255, 255, 0.5);
  }

  .footer-legal {
    display: flex;
    gap: var(--space-md);
  }

  .footer-legal a {
    font-size: var(--text-sm);
    color: rgba(255, 255, 255, 0.5);
    text-decoration: none;
    transition: color var(--transition-fast);
  }

  .footer-legal a:hover {
    color: var(--color-light);
  }
</style>
