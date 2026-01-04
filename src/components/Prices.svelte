<script>
// @ts-nocheck

  let check = '<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="#f4a484" viewBox="0 0 256 256"><path d="M173.66,98.34a8,8,0,0,1,0,11.32l-56,56a8,8,0,0,1-11.32,0l-24-24a8,8,0,0,1,11.32-11.32L112,148.69l50.34-50.35A8,8,0,0,1,173.66,98.34ZM232,128A104,104,0,1,1,128,24,104.11,104.11,0,0,1,232,128Zm-16,0a88,88,0,1,0-88,88A88.1,88.1,0,0,0,216,128Z"></path></svg>'
  
  const packages = [
    {
      id: '01',
      name: 'Essential',
      price: '£800',
      timeline: '2-3 weeks',
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="#f4a484" viewBox="0 0 256 256"><path d="M224,48H32A16,16,0,0,0,16,64V192a16,16,0,0,0,16,16H224a16,16,0,0,0,16-16V64A16,16,0,0,0,224,48Zm0,144H32V64H224V192ZM112,88a8,8,0,0,1,8-8h96a8,8,0,0,1,0,16H120A8,8,0,0,1,112,88Zm0,40a8,8,0,0,1,8-8h96a8,8,0,0,1,0,16H120A8,8,0,0,1,112,128Zm0,40a8,8,0,0,1,8-8h96a8,8,0,0,1,0,16H120A8,8,0,0,1,112,168ZM72,96a8,8,0,1,1-8-8A8,8,0,0,1,72,96Zm0,40a8,8,0,1,1-8-8A8,8,0,0,1,72,136Zm0,40a8,8,0,1,1-8-8A8,8,0,0,1,72,176Z"></path></svg>',
      description: 'Perfect for small businesses and startups looking to establish a professional online presence. A clean, responsive website that showcases your brand with essential features and functionality.',
      features: [
        'Up to 5 Custom Pages',
        'Responsive Design (Mobile, Tablet, Desktop)',
        'Contact Form Integration',
        'Basic SEO Setup',
        'Google Analytics Integration',
        'Social Media Integration',
        '1 Month Post-Launch Support',
        'SSL Certificate Included'
      ]
    },
    {
      id: '02',
      name: 'Pro',
      price: '£1,500',
      timeline: '4-6 weeks',
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="#f4a484" viewBox="0 0 256 256"><path d="M247.31,124.76c-.35-.79-8.82-19.58-27.65-38.41C194.57,61.26,162.88,48,128,48S61.43,61.26,36.34,86.35C17.51,105.18,9,124,8.69,124.76a8,8,0,0,0,0,6.5c.35.79,8.82,19.57,27.65,38.4C61.43,194.74,93.12,208,128,208s66.57-13.26,91.66-38.34c18.83-18.83,27.3-37.61,27.65-38.4A8,8,0,0,0,247.31,124.76ZM128,192c-30.78,0-57.67-11.19-79.93-33.25A133.47,133.47,0,0,1,25,128,133.33,133.33,0,0,1,48.07,97.25C70.33,75.19,97.22,64,128,64s57.67,11.19,79.93,33.25A133.46,133.46,0,0,1,231.05,128C223.84,141.46,192.43,192,128,192Zm0-112a48,48,0,1,0,48,48A48.05,48.05,0,0,0,128,80Zm0,80a32,32,0,1,1,32-32A32,32,0,0,1,128,160Z"></path></svg>',
      description: 'Comprehensive solution for growing businesses that need advanced functionality and scalability. Custom-built with powerful features including content management, e-commerce capabilities, and database integration.',
      features: [
        'Up to 15 Custom Pages',
        'Custom CMS Integration (Easy Content Updates)',
        'Database Integration & User Authentication',
        'E-commerce Functionality (Products, Cart, Checkout)',
        'Advanced SEO & Performance Optimization',
        'Email Marketing Integration',
        'Custom Forms & Dynamic Features',
        'Payment Gateway Integration (Stripe/PayPal)',
        'Blog System with Categories & Tags',
        'Advanced Analytics & Reporting',
        '3 Months Post-Launch Support & Maintenance',
        'Priority Support & Updates'
      ]
    }
  ];
</script>

<section>
<div class="container">
  <div class="pricing-grid">
    {#each packages as pkg}
      <div class="pricing-card">
        <div class="card-header">
          <div class="title-row">
            {@html pkg.icon}
            <h3>{pkg.name}</h3>
          </div>
          <div class="price">{pkg.price}</div>
          <div class="timeline">{pkg.timeline}</div>
        </div>
        
        <div class="card-description">
          <p>{pkg.description}</p>
        </div>
        
        <div class="card-features">
          <ul>
            {#each pkg.features as feature}
              <li>{@html check} {feature}</li>
            {/each}
          </ul>
        </div>
      </div>
    {/each}
  </div>
</div>
</section>


<style>

    section{
        display: flex;
        justify-content: center;
    }
  .container {
    width: 95%;
    grid-column: span 12;
    margin-top: 1rem;
  }

  .pricing-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: .5rem;
  }

  .pricing-card {
    border: 1px solid #ffffff89;
    padding: 2rem;
    display: flex;
    flex-direction: column;

  }

  .pricing-card:last-child {
    border: 2px solid #f4a484;
    background: rgba(244, 164, 132, 0.05);
    position: relative;
  }

  .pricing-card:last-child::before {
    content: 'POPULAR';
    position: absolute;
    top: -12px;
    right: 2rem;
    background: #f4a484;
    color: #000000;
    padding: 0.25rem 1rem;
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.05em;
  }

  .card-header {
    border-bottom: 1px solid #ffffff;
    padding-bottom: 1.5rem;
    margin-bottom: 1.5rem;
  }

  .title-row {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-bottom: 1rem;
  }

  .title-row h3 {
    margin: 0;
    text-transform: uppercase;
    font-size: 1.25rem;
    color: #ffffff;
  }

  .price {
    color: #f4a484;
    font-size: 2rem;
    font-weight: 600;
    margin-bottom: 0.5rem;
  }

  .timeline {
    color: #ffffff;
    opacity: 0.7;
    font-size: 0.875rem;
  }

  .card-description {
    margin-bottom: 1.5rem;
  }

  .card-description p {
    color: #ffffff;
    line-height: 1.6;
    margin: 0;
  }

  .card-features ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .card-features li {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    margin-bottom: 0.75rem;
    color: #ffffff;
  }

  .card-features li:last-child {
    margin-bottom: 0;
  }

  @media (max-width: 768px) {
    .pricing-grid {
      grid-template-columns: 1fr;
    }
  }
</style>