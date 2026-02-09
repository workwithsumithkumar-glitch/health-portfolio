<script lang="ts">
  let formData = $state({
    name: '',
    phone: '',
    childAge: '',
    concern: '',
    preferredTime: '',
  });

  let submitting = $state(false);
  let submitted = $state(false);

  async function handleSubmit(e: Event) {
    e.preventDefault();
    submitting = true;

    // Simulate form submission
    await new Promise(resolve => setTimeout(resolve, 1500));

    submitting = false;
    submitted = true;

    // Reset after showing success
    setTimeout(() => {
      submitted = false;
      formData = {
        name: '',
        phone: '',
        childAge: '',
        concern: '',
        preferredTime: '',
      };
    }, 5000);
  }
</script>

<section id="contact" class="contact section">
  <div class="container">
    <div class="contact-grid">
      <div class="contact-info">
        <h2>Let's Start the Conversation</h2>
        <p class="contact-intro">
          Every journey begins with a single step. Reach out, and let's write a beautiful chapter together.
        </p>

        <div class="info-cards">
          <div class="info-card">
            <div class="info-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/>
                <circle cx="12" cy="10" r="3"/>
              </svg>
            </div>
            <div class="info-content">
              <h4>Location</h4>
              <p>Medanta Hospital<br/>Indore, Madhya Pradesh</p>
            </div>
          </div>

          <div class="info-card">
            <div class="info-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/>
              </svg>
            </div>
            <div class="info-content">
              <h4>Phone</h4>
              <p><a href="tel:+918839708182">+91 8839708182</a></p>
            </div>
          </div>

          <div class="info-card">
            <div class="info-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
                <polyline points="22,6 12,13 2,6"/>
              </svg>
            </div>
            <div class="info-content">
              <h4>Email</h4>
              <p><a href="mailto:rachnadube@gmail.com">rachnadube@gmail.com</a></p>
            </div>
          </div>

          <div class="info-card">
            <div class="info-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <circle cx="12" cy="12" r="10"/>
                <polyline points="12 6 12 12 16 14"/>
              </svg>
            </div>
            <div class="info-content">
              <h4>Hours</h4>
              <p>Monday - Saturday<br/>10:00 AM - 6:00 PM</p>
            </div>
          </div>
        </div>

        <a href="https://wa.me/918839708182" class="whatsapp-btn" target="_blank" rel="noopener noreferrer">
          <svg viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
            <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/>
          </svg>
          Chat on WhatsApp
        </a>
      </div>

      <div class="contact-form-wrapper">
        <div class="form-card">
          <h3>Book a Consultation</h3>

          {#if submitted}
            <div class="success-message">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/>
                <polyline points="22 4 12 14.01 9 11.01"/>
              </svg>
              <h4>Thank you!</h4>
              <p>We've received your request and will contact you soon.</p>
            </div>
          {:else}
            <form onsubmit={handleSubmit}>
              <div class="form-group">
                <label for="name" class="form-label">Your Name *</label>
                <input
                  type="text"
                  id="name"
                  class="form-input"
                  placeholder="Enter your full name"
                  bind:value={formData.name}
                  required
                />
              </div>

              <div class="form-group">
                <label for="phone" class="form-label">Phone Number *</label>
                <input
                  type="tel"
                  id="phone"
                  class="form-input"
                  placeholder="+91 XXXXX XXXXX"
                  bind:value={formData.phone}
                  required
                />
              </div>

              <div class="form-row">
                <div class="form-group">
                  <label for="childAge" class="form-label">Child's Age</label>
                  <input
                    type="text"
                    id="childAge"
                    class="form-input"
                    placeholder="e.g., 5 years"
                    bind:value={formData.childAge}
                  />
                </div>

                <div class="form-group">
                  <label for="preferredTime" class="form-label">Preferred Time</label>
                  <select id="preferredTime" class="form-input" bind:value={formData.preferredTime}>
                    <option value="">Select time</option>
                    <option value="morning">Morning (10-12)</option>
                    <option value="afternoon">Afternoon (12-3)</option>
                    <option value="evening">Evening (3-6)</option>
                  </select>
                </div>
              </div>

              <div class="form-group">
                <label for="concern" class="form-label">Briefly describe your concern</label>
                <textarea
                  id="concern"
                  class="form-textarea"
                  placeholder="Help us understand how we can help..."
                  bind:value={formData.concern}
                  rows="4"
                ></textarea>
              </div>

              <button type="submit" class="btn btn-primary submit-btn" disabled={submitting}>
                {#if submitting}
                  <span class="spinner"></span>
                  Sending...
                {:else}
                  Request Appointment
                {/if}
              </button>
            </form>
          {/if}
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .contact {
    background: var(--surface-secondary);
  }

  .contact-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: var(--space-xl);
  }

  @media (min-width: 768px) {
    .contact-grid {
      grid-template-columns: 1fr 1fr;
      gap: var(--space-2xl);
    }
  }

  .contact-info h2 {
    margin-bottom: var(--space-md);
  }

  .contact-intro {
    font-size: var(--text-lg);
    color: var(--text-secondary);
    margin-bottom: var(--space-xl);
  }

  .info-cards {
    display: grid;
    grid-template-columns: 1fr;
    gap: var(--space-md);
    margin-bottom: var(--space-lg);
  }

  @media (min-width: 480px) {
    .info-cards {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  .info-card {
    display: flex;
    gap: var(--space-md);
    padding: var(--space-md);
    background: var(--surface-primary);
    border-radius: var(--radius-md);
    transition: all var(--transition-fast);
    border: 1px solid var(--border-light);
  }

  .info-card:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow-md);
  }

  .info-icon {
    width: 40px;
    height: 40px;
    padding: 8px;
    background: color-mix(in srgb, var(--color-primary) 10%, transparent);
    border-radius: var(--radius-sm);
    color: var(--color-primary);
    flex-shrink: 0;
  }

  .info-icon svg {
    width: 100%;
    height: 100%;
  }

  .info-content h4 {
    font-size: var(--text-sm);
    font-weight: 600;
    color: var(--text-primary);
    margin-bottom: 2px;
  }

  .info-content p {
    font-size: var(--text-sm);
    color: var(--text-muted);
    line-height: 1.5;
  }

  .info-content a {
    color: var(--color-primary);
  }

  .info-content a:hover {
    color: var(--color-secondary);
  }

  .whatsapp-btn {
    display: inline-flex;
    align-items: center;
    gap: var(--space-sm);
    padding: var(--space-md) var(--space-lg);
    background: #25D366;
    color: white;
    border-radius: var(--radius-full);
    font-weight: 600;
    transition: all var(--transition-base);
  }

  .whatsapp-btn:hover {
    background: #128C7E;
    color: white;
    transform: translateY(-2px);
  }

  .form-card {
    background: var(--surface-primary);
    border-radius: var(--radius-xl);
    padding: var(--space-xl);
    box-shadow: var(--shadow-lg);
    border: 1px solid var(--border-light);
  }

  .form-card h3 {
    font-size: var(--text-2xl);
    margin-bottom: var(--space-lg);
    color: var(--text-primary);
  }

  .form-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: var(--space-md);
  }

  @media (max-width: 480px) {
    .form-row {
      grid-template-columns: 1fr;
    }
  }

  .submit-btn {
    width: 100%;
    margin-top: var(--space-md);
  }

  .spinner {
    width: 18px;
    height: 18px;
    border: 2px solid transparent;
    border-top-color: currentColor;
    border-radius: 50%;
    animation: spin 0.8s linear infinite;
  }

  @keyframes spin {
    to { transform: rotate(360deg); }
  }

  .success-message {
    text-align: center;
    padding: var(--space-xl);
  }

  .success-message svg {
    width: 64px;
    height: 64px;
    color: var(--success);
    margin-bottom: var(--space-md);
  }

  .success-message h4 {
    font-size: var(--text-xl);
    color: var(--text-primary);
    margin-bottom: var(--space-sm);
  }

  .success-message p {
    color: var(--text-secondary);
  }
</style>
