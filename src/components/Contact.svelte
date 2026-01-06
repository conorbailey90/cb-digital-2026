<script>
  // @ts-nocheck
  import Container from "./Container.svelte";

  let formData = {
    name: '',
    email: '',
    company: '',
    service: '',
    message: ''
  };

  let isSubmitting = false;
  let submitStatus = null;

  const services = [
    'Web Design',
    'Web Development',
    'Web Design & Development',
    'Hosting',
    'Digital Strategy',
    'Other'
  ];

  async function handleSubmit(e) {
    e.preventDefault();
    isSubmitting = true;
    submitStatus = null;

    try {
      const response = await fetch('https://formspree.io/f/xbdlnjoa', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(formData)
      });

      if (response.ok) {
        isSubmitting = false;
        submitStatus = 'success';
        alert('Many thanks for your message. We will be in touch soon!')
        
        // Reset form after successful submission
        formData = {
          name: '',
          email: '',
          company: '',
          service: '',
          message: ''
        };

        // Clear success message after 5 seconds
        setTimeout(() => {
          submitStatus = null;
        }, 5000);
      } else {
        throw new Error('Failed to send message');
      }
    } catch (error) {
      isSubmitting = false;
      submitStatus = 'error';
      console.error('Form submission error:', error);
      
      // Clear error message after 5 seconds
      setTimeout(() => {
        submitStatus = null;
      }, 5000);
    }
  }
</script>

<section id="contact" data-bg-color="#000000" data-text-color="#FFFFFF">
  <Container>
    <div class="header">
      <h4>Get In Touch</h4>
    </div>
    <div class="line"></div>

    <div class="contact-wrapper">
      <div class="contact-info">
        <h2>Let's Build Something Great Together</h2>
        <p>Ready to start your project? Fill out the form and I'll get back to you within 24 hours.</p>
        
        <div class="info-items">
          <div class="info-item">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="#f4a484" viewBox="0 0 256 256">
              <path d="M224,48H32a8,8,0,0,0-8,8V192a8,8,0,0,0,8,8H224a8,8,0,0,0,8-8V56A8,8,0,0,0,224,48Zm-96,85.15L52.57,64H203.43ZM98.71,128,40,181.81V74.19Zm11.84,10.85,12,11.05a8,8,0,0,0,10.82,0l12-11.05,58,53.15H52.57ZM157.29,128,216,74.18V181.82Z"></path>
            </svg>
            <div>
              <h5>Email</h5>
              <a href="mailto:hello@example.com">conbailey90@gmail.com</a>
            </div>
          </div>

          <div class="info-item">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="#f4a484" viewBox="0 0 256 256">
              <path d="M128,64a40,40,0,1,0,40,40A40,40,0,0,0,128,64Zm0,64a24,24,0,1,1,24-24A24,24,0,0,1,128,128Zm0-112a88.1,88.1,0,0,0-88,88c0,31.4,14.51,64.68,42,96.25a254.19,254.19,0,0,0,41.45,38.3,8,8,0,0,0,9.18,0A254.19,254.19,0,0,0,174,200.25c27.45-31.57,42-64.85,42-96.25A88.1,88.1,0,0,0,128,16Zm0,206c-16.53-13-72-60.75-72-118a72,72,0,0,1,144,0C200,161.23,144.53,209,128,222Z"></path>
            </svg>
            <div>
              <h5>Location</h5>
              <p>Billericay, Essex, UK</p>
            </div>
          </div>
        </div>
      </div>

      <form class="contact-form" on:submit={handleSubmit}>
        <div class="form-row">
          <div class="form-group">
            <label for="name">Name *</label>
            <input 
              type="text" 
              id="name" 
              bind:value={formData.name}
              required
            />
          </div>

          <div class="form-group">
            <label for="email">Email *</label>
            <input 
              type="email" 
              id="email" 
              bind:value={formData.email}
              required
            />
          </div>
        </div>

        <div class="form-row">
          <div class="form-group">
            <label for="company">Company</label>
            <input 
              type="text" 
              id="company" 
              bind:value={formData.company}
            />
          </div>

          <div class="form-group">
            <label for="service">Service Interested In *</label>
            <select 
              id="service" 
              bind:value={formData.service}
              required
            >
              <option value="">Select a service</option>
              {#each services as service}
                <option value={service}>{service}</option>
              {/each}
            </select>
          </div>
        </div>

        <div class="form-group">
          <label for="message">Message *</label>
          <textarea 
            id="message" 
            rows="6"
            bind:value={formData.message}
            required
          ></textarea>
        </div>

        <button 
          type="submit" 
          class="submit-btn"
          disabled={isSubmitting}
        >
          {#if isSubmitting}
            Sending...
          {:else}
            Send Message
          {/if}
        </button>

        {#if submitStatus === 'success'}
          <div class="success-message">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="#f4a484" viewBox="0 0 256 256">
              <path d="M173.66,98.34a8,8,0,0,1,0,11.32l-56,56a8,8,0,0,1-11.32,0l-24-24a8,8,0,0,1,11.32-11.32L112,148.69l50.34-50.35A8,8,0,0,1,173.66,98.34ZM232,128A104,104,0,1,1,128,24,104.11,104.11,0,0,1,232,128Zm-16,0a88,88,0,1,0-88,88A88.1,88.1,0,0,0,216,128Z"></path>
            </svg>
            Message sent successfully! I'll get back to you soon.
          </div>
        {/if}

        {#if submitStatus === 'error'}
          <div class="error-message">
            <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="#ff6b6b" viewBox="0 0 256 256">
              <path d="M128,24A104,104,0,1,0,232,128,104.11,104.11,0,0,0,128,24Zm0,192a88,88,0,1,1,88-88A88.1,88.1,0,0,1,128,216Zm-8-80V80a8,8,0,0,1,16,0v56a8,8,0,0,1-16,0Zm20,36a12,12,0,1,1-12-12A12,12,0,0,1,140,172Z"></path>
            </svg>
            Failed to send message. Please try again.
          </div>
        {/if}
      </form>
    </div>
  </Container>
</section>

<style>
  section {
    display: flex;
    justify-content: center;
    padding: 80px 0 2rem 0;
  }

  .header {
    display: flex;
    grid-column: span 12;
  }

  .line {
    grid-column: span 12;
    height: 1px;
    background: rgba(255, 255, 255, 0.1);
    margin-bottom: 3rem;
  }

  .contact-wrapper {
    grid-column: span 12;
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    gap: 2rem;
  }

  .contact-info {
    grid-column: span 5;
  }

  .contact-info h2 {
    font-size: 2rem;
    font-weight: 500;
    margin: 0 0 1rem 0;
    line-height: 1.2;
    letter-spacing: -0.02em;
  }

  .contact-info p {
    color: rgba(255, 255, 255, 0.7);
    line-height: 1.6;
    margin-bottom: 2rem;
  }

  .info-items {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }

  .info-item {
    display: flex;
    align-items: flex-start;
    gap: 1rem;
  }

  .info-item svg {
    flex-shrink: 0;
    margin-top: 0.25rem;
  }

  .info-item h5 {
    margin: 0 0 0.25rem 0;
    font-size: 0.875rem;
    font-weight: 500;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    color: #f4a484;
  }

  .info-item p,
  .info-item a {
    margin: 0;
    color: rgba(255, 255, 255, 0.7);
    text-decoration: none;
    transition: color 0.3s ease;
  }

  .info-item a:hover {
    color: #f4a484;
  }

  .contact-form {
    grid-column: 7 / span 6;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }

  .form-row {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1.5rem;
  }

  .form-group {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  label {
    font-size: 0.875rem;
    color: rgba(255, 255, 255, 0.9);
    font-weight: 500;
  }

  input,
  select,
  textarea {
    background: rgba(255, 255, 255, 0.02);
    border: 1px solid rgba(255, 255, 255, 0.1);
    color: white;
    padding: 0.875rem 1rem;
    font-size: 1rem;
    font-family: inherit;
    transition: all 0.3s ease;
  }

  input:focus,
  select:focus,
  textarea:focus {
    outline: none;
    border-color: #f4a484;
    background: rgba(255, 255, 255, 0.05);
  }

  select {
    cursor: pointer;
  }

  textarea {
    resize: vertical;
    min-height: 120px;
  }

  .submit-btn {
    background: #f4a484;
    color: #000000;
    border: none;
    padding: 1rem 2rem;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    width: fit-content;
  }

  .submit-btn:hover:not(:disabled) {
    background: #ffffff;
    transform: translateY(-2px);
  }

  .submit-btn:disabled {
    opacity: 0.6;
    cursor: not-allowed;
  }

  .success-message {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 1rem;
    background: rgba(244, 164, 132, 0.1);
    border: 1px solid #f4a484;
    color: #f4a484;
    font-size: 0.875rem;
  }

  .error-message {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 1rem;
    background: rgba(255, 107, 107, 0.1);
    border: 1px solid #ff6b6b;
    color: #ff6b6b;
    font-size: 0.875rem;
  }

  /* Tablet */
  @media (max-width: 1024px) {
    .contact-wrapper {
      grid-template-columns: 1fr;
    }

    .contact-info,
    .contact-form {
      grid-column: span 12;
    }

    .contact-info {
      margin-bottom: 2rem;
    }
  }

  /* Mobile */
  @media (max-width: 768px) {
    section {
      padding: 4rem 0;
    }

    .contact-info h2 {
      font-size: 1.5rem;
    }

    .form-row {
      grid-template-columns: 1fr;
      gap: 1.5rem;
    }
  }
</style>