<script>
  import { slide } from "svelte/transition";
  
  let openId = null;
  
  const services = [
    {
      id: '01',
      title: 'Web Design',
      description: 'Beautiful, user-centered designs that reflect your brand identity. Modern aesthetics with intuitive navigation and responsive layouts across all devices.'
    },
    {
      id: '02',
      title: 'Web Development',
      description: 'Robust, scalable websites using cutting-edge technologies. Clean code, optimal performance, and seamless functionality from landing pages to complex applications.'
    },
    {
      id: '03',
      title: 'Hosting',
      description: 'Reliable, secure hosting with 99.9% uptime. Managed services including automatic backups, SSL certificates, and 24/7 monitoring.'
    },
    {
      id: '04',
      title: 'Digital Strategy',
      description: 'Data-driven strategies that drive growth. SEO, content marketing, analytics, and conversion optimization to maximize your online presence.'
    }
  ];
  
  function toggle(id) {
    openId = openId === id ? null : id;
  }
</script>

<div class="container">
  
  <div class="accordion">
    {#each services as service}
      <div class="accordion-item">
        <button 
          class="accordion-header" 
          onclick={() => toggle(service.id)}
        >
            <p>
                <span style="margin-right: 1rem;">{service.id} </span>
                <span>{service.title}</span>
            </p>
         
            <svg 
                class="chevron" 
                class:rotated={openId === service.id}
                width="20" 
                height="20" 
                viewBox="0 0 24 24" 
                fill="none" 
                stroke="currentColor" 
                stroke-width="2"
            >
                <polyline points="6 9 12 15 18 9"></polyline>
            </svg>
        </button>
        
        {#if openId === service.id}
          <div class="accordion-content" transition:slide={{ duration: 500 }}>
            <p>{service.description}</p>
          </div>
        {/if}
      </div>
    {/each}
  </div>
</div>

<style>
  .container {
    grid-column: span 12;
    min-height: 100vh;
    margin-top: 1rem;
    /* background: rgb(0, 0, 0); */
   
  }
  
  .accordion {
    border-top: 1px solid #ffffff;
  }
  
  .accordion-item {
    border-bottom: 1px solid #ffffff;
  }
  
  .accordion-header {
    width: 100%;
    padding: 1.5rem 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: none;
    border: none;
    cursor: pointer;
    font-size: 1.125rem;
    color: #111;
    text-align: left;
  }
  
  .accordion-header:hover {
    opacity: 0.7;
  }
  
  .chevron {
    color: #ffffff;
    transition: transform 200ms ease;
  }
  
  .chevron.rotated {
    transform: rotate(180deg);
  }
  
  .accordion-content {
    padding-bottom: 1.5rem;
    overflow: hidden;
  }
  
  .accordion-content p {
    color: #ffffff;
    margin: 0;
  }
</style>