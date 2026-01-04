<script>
// @ts-nocheck


import { slide } from "svelte/transition";
  let check = '<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="#f4a484" viewBox="0 0 256 256"><path d="M173.66,98.34a8,8,0,0,1,0,11.32l-56,56a8,8,0,0,1-11.32,0l-24-24a8,8,0,0,1,11.32-11.32L112,148.69l50.34-50.35A8,8,0,0,1,173.66,98.34ZM232,128A104,104,0,1,1,128,24,104.11,104.11,0,0,1,232,128Zm-16,0a88,88,0,1,0-88,88A88.1,88.1,0,0,0,216,128Z"></path></svg>'
  
  /**
	 * @type {number | null}
	 */
  let openId = null;
  
  const services = [
    {
      id: '01',
      title: 'Web Design',
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="#f4a484" viewBox="0 0 256 256"><path d="M215.12,123.64a8,8,0,1,0-14.24-7.28,79.58,79.58,0,0,1-33.08,33.5l-16.58-37.32A40,40,0,0,0,136,40.8V24a8,8,0,0,0-16,0V40.8a40,40,0,0,0-15.22,71.74L56.69,220.75a8,8,0,1,0,14.62,6.5l25.14-56.56A95.48,95.48,0,0,0,128,176a99.13,99.13,0,0,0,31.6-5.21l25.09,56.46a8,8,0,0,0,14.62-6.5l-25-56.25A95.81,95.81,0,0,0,215.12,123.64ZM128,56a24,24,0,1,1-24,24A24,24,0,0,1,128,56Zm0,104a79.52,79.52,0,0,1-25-4l16.42-36.94a39.81,39.81,0,0,0,17.2,0l16.48,37.06A83.21,83.21,0,0,1,128,160Z"></path></svg>',
      description: '<p>Strategic design solutions that elevate your brand and engage your audience through thoughtful user experiences and UI/UX design. <br><br> We specialize in crafting clean, minimal, and functional websites that put your business/brand front and center. My focus is on creating intuitive, user-friendly designs with sleek UI/UX that drive engagement and deliver results.</p>',
      included: [
        'Clean & Impactful Brand Identity',
        'Intuitive User Experience (UX) Design',
        'Responsive & Streamlined Design Systems to Work on All Devices',
        'Strategic Wireframing & Prototyping'
      ]
    },
    {
      id: '02',
      title: 'Web Development',
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="#f4a484" viewBox="0 0 256 256"><path d="M69.12,94.15,28.5,128l40.62,33.85a8,8,0,1,1-10.24,12.29l-48-40a8,8,0,0,1,0-12.29l48-40a8,8,0,0,1,10.24,12.3Zm176,27.7-48-40a8,8,0,1,0-10.24,12.3L227.5,128l-40.62,33.85a8,8,0,1,0,10.24,12.29l48-40a8,8,0,0,0,0-12.29ZM162.73,32.48a8,8,0,0,0-10.25,4.79l-64,176a8,8,0,0,0,4.79,10.26A8.14,8.14,0,0,0,96,224a8,8,0,0,0,7.52-5.27l64-176A8,8,0,0,0,162.73,32.48Z"></path></svg>',
      description: '<p>Robust, scalable websites using cutting-edge technologies. Clean code, optimal performance, and seamless functionality from landing pages to complex applications.<br><br> We develop custom websites and web applications with tailored features designed to meet your unique needs, emphasizing clean, minimal, and functional design. Using modern technologies and best practices, we deliver fast, reliable, and high-performing solutions that drive results.</p>',
      included: [
        'Custom-Built Website with Fast Loading Speeds',
        'Built-In SEO Foundations for Better Search Visibility',
        'Easy Integration with Tools like Email Signup & Online Payments',
        'Simple Content Management System for Easy Updates'
      ]
    },
    {
      id: '03',
      title: 'Hosting',
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="#f4a484" viewBox="0 0 256 256"><path d="M208,136H48a16,16,0,0,0-16,16v48a16,16,0,0,0,16,16H208a16,16,0,0,0,16-16V152A16,16,0,0,0,208,136Zm0,64H48V152H208v48Zm0-160H48A16,16,0,0,0,32,56v48a16,16,0,0,0,16,16H208a16,16,0,0,0,16-16V56A16,16,0,0,0,208,40Zm0,64H48V56H208v48ZM192,80a12,12,0,1,1-12-12A12,12,0,0,1,192,80Zm0,96a12,12,0,1,1-12-12A12,12,0,0,1,192,176Z"></path></svg>',
      description: '<p>Reliable, secure hosting with 99.9% uptime. Managed services including automatic backups, SSL certificates, and 24/7 monitoring.<br><br>We provide reliable, secure web hosting with fast performance and 24/7 monitoring, ensuring your website stays online and runs smoothly for your peace of mind.</p>',
      included: [
        '99.9% Uptime Guarantee for Always-On Availability',
        'Easy Website Management Tools',
        'Fast & Reliable Website Performance',
        'Scalable Plans That Grow with Your Business'
      ]
    },
    {
      id: '04',
      title: 'Digital Strategy',
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="#f4a484" viewBox="0 0 256 256"><path d="M76,152a36,36,0,1,0,36,36A36,36,0,0,0,76,152Zm0,56a20,20,0,1,1,20-20A20,20,0,0,1,76,208ZM42.34,106.34,56.69,92,42.34,77.66A8,8,0,0,1,53.66,66.34L68,80.69,82.34,66.34A8,8,0,0,1,93.66,77.66L79.31,92l14.35,14.34a8,8,0,0,1-11.32,11.32L68,103.31,53.66,117.66a8,8,0,0,1-11.32-11.32Zm187.32,96a8,8,0,0,1-11.32,11.32L204,199.31l-14.34,14.35a8,8,0,0,1-11.32-11.32L192.69,188l-14.35-14.34a8,8,0,0,1,11.32-11.32L204,176.69l14.34-14.35a8,8,0,0,1,11.32,11.32L215.31,188Zm-45.19-89.51c-6.18,22.33-25.32,41.63-46.53,46.93A8.13,8.13,0,0,1,136,160a8,8,0,0,1-1.93-15.76c15.63-3.91,30.35-18.91,35-35.68,3.19-11.5,3.22-29-14.71-46.9L152,59.31V80a8,8,0,0,1-16,0V40a8,8,0,0,1,8-8h40a8,8,0,0,1,0,16H163.31l2.35,2.34C183.9,68.59,190.58,90.78,184.47,112.83Z"></path></svg>',
      description: '<p>Data-driven strategies that drive growth. SEO, content marketing, analytics, and conversion optimization to maximize your online presence.<br><br> We create simple, effective plans to boost your online presence, making your website easier to find on search engines and tailored to help your business grow.</p>',
      included: [
        'On-Page SEO Setup to Attract Local Customers',
        'Analytics & Performance Tracking',
        'Google Analytics Integration for Traffic Insights'
      ]
    }
  ];
  
  /**
	 * @param {string | number | null} id
	 */
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
                <!-- <span style="margin-right: 1rem;">{service.id} </span> -->
                {@html service.icon}
                <span style="text-transform: uppercase"> {service.title}</span>
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
            <div class="service__description">
                {@html service.description}
            </div>
            <div class="included">
              <ul>
                {#each service.included as item}
                  <li>{@html check} {item}</li>
                {/each}
              </ul>
            </div>
          
          </div>
        {/if}
      </div>
    {/each}
  </div>
</div>

<style>
  .container {
  grid-column: span 12;

  margin-top: 1rem;
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
  align-items: center; /* Vertically centers the <p> and chevron */
  justify-content: space-between;
  background: none;
  border: none;
  cursor: pointer;
  font-size: 1.125rem;
  text-align: left;
}

.accordion-header p {
  display: flex; /* Makes icon and title flex items */
  align-items: center; /* Vertically centers icon with title text */
  gap: 1rem; /* Horizontal space between icon and title (adjust as needed) */
  margin: 0; /* Reset any default p margins */


}

.accordion-header svg:first-of-type { /* Targets the service icon SVGs */
  flex-shrink: 0; /* Prevents icon from shrinking */
  display: inline-block; /* Ensures consistent inline rendering */
}

.accordion-header:hover {
  opacity: 0.7;
}

.chevron {
  color: #ffffff;
  transition: transform 200ms ease;
  flex-shrink: 0; /* Prevents chevron from shrinking */
}

.chevron.rotated {
  transform: rotate(180deg);
}

.accordion-content {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: .5rem;
  padding-bottom: 1.5rem;
  overflow: hidden;
}

.service__description{
  grid-column: span 5;
}

.included{
  grid-column: 7 / span 6;
}

.accordion-content p {
  color: #ffffff;
  margin: 0;

}

.included ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.included li {
  display: flex;
  align-items: center;
  gap: 0.5rem; /* Adjust space between check and text as needed */
  margin-bottom: 0.5rem; /* Space between list items */
  color: #ffffff;
}

.included li svg {
  flex-shrink: 0; /* Prevents check from shrinking */
  display: inline-block;
}

.included li:last-child {
  margin-bottom: 0;
}
</style>