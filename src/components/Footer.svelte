<script>
    import Container from "./Container.svelte";
    import { base } from "$app/paths";
   const navigation = [
        {name: 'Home', link: `${base}/#home`},
        {name: 'About', link: `${base}/#about`},
        {name: 'Services', link: `${base}/#services`},
        {name: 'Projects', link: `${base}/#projects`},
        {name: 'Contact', link: `${base}/#contact`},
    ];

    const socials = [
        {
            name: 'LinkedIn',
            link: 'https://linkedin.com',
            icon: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 256 256"><path d="M216,24H40A16,16,0,0,0,24,40V216a16,16,0,0,0,16,16H216a16,16,0,0,0,16-16V40A16,16,0,0,0,216,24Zm0,192H40V40H216V216ZM96,112v64a8,8,0,0,1-16,0V112a8,8,0,0,1,16,0Zm88,28v36a8,8,0,0,1-16,0V140a20,20,0,0,0-40,0v36a8,8,0,0,1-16,0V112a8,8,0,0,1,15.79-1.78A36,36,0,0,1,184,140ZM100,84A12,12,0,1,1,88,72,12,12,0,0,1,100,84Z"></path></svg>'
        },
        {
            name: 'GitHub',
            link: 'https://github.com',
            icon: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 256 256"><path d="M208.31,75.68A59.78,59.78,0,0,0,202.93,28,8,8,0,0,0,196,24a59.75,59.75,0,0,0-48,24H124A59.75,59.75,0,0,0,76,24a8,8,0,0,0-6.93,4,59.78,59.78,0,0,0-5.38,47.68A58.14,58.14,0,0,0,56,104v8a56.06,56.06,0,0,0,48.44,55.47A39.8,39.8,0,0,0,96,192v8H72a24,24,0,0,1-24-24A40,40,0,0,0,8,136a8,8,0,0,0,0,16,24,24,0,0,1,24,24,40,40,0,0,0,40,40H96v16a8,8,0,0,0,16,0V192a24,24,0,0,1,48,0v40a8,8,0,0,0,16,0V192a39.8,39.8,0,0,0-8.44-24.53A56.06,56.06,0,0,0,216,112v-8A58.14,58.14,0,0,0,208.31,75.68ZM200,112a40,40,0,0,1-40,40H112a40,40,0,0,1-40-40v-8a41.74,41.74,0,0,1,6.9-22.48,8,8,0,0,0,1.1-7.69,43.81,43.81,0,0,1,.79-33.58,43.88,43.88,0,0,1,32.32,20.06A8,8,0,0,0,119.82,64h32.35a8,8,0,0,0,6.74-3.69,43.87,43.87,0,0,1,32.32-20.06A43.81,43.81,0,0,1,192,73.83a8.09,8.09,0,0,0,1,7.65A41.72,41.72,0,0,1,200,104Z"></path></svg>'
        },
        {
            name: 'Twitter',
            link: 'https://twitter.com',
            icon: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 256 256"><path d="M247.39,68.94A8,8,0,0,0,240,64H209.57A48.66,48.66,0,0,0,168.1,40a46.91,46.91,0,0,0-33.75,13.7A47.9,47.9,0,0,0,120,88v6.09C79.74,83.47,46.81,50.72,46.46,50.37a8,8,0,0,0-13.65,4.92c-4.31,47.79,9.57,79.77,22,98.18a110.93,110.93,0,0,0,21.88,24.2c-15.23,17.53-39.21,26.74-39.47,26.84a8,8,0,0,0-3.85,11.93c.75,1.12,3.75,5.05,11.08,8.72C53.51,229.7,65.48,232,80,232c70.67,0,129.72-54.42,135.75-124.44l29.91-29.9A8,8,0,0,0,247.39,68.94Zm-45,29.41a8,8,0,0,0-2.32,5.14C196,166.58,143.28,216,80,216c-10.56,0-18-1.4-23.22-3.08,11.51-6.25,27.56-17,37.88-32.48A8,8,0,0,0,92,169.08c-.47-.27-43.91-26.34-44-96,16,13,45.25,33.17,78.67,38.79A8,8,0,0,0,136,104V88a32,32,0,0,1,9.6-22.92A30.94,30.94,0,0,1,167.9,56c12.66.16,24.49,7.88,29.44,19.21A8,8,0,0,0,204.67,80h16Z"></path></svg>'
        }
    ];

    const currentYear = new Date().getFullYear();
</script>

<style>
    footer {
        display: flex;
        justify-content: center;
        width: 100%;
        border-top: 1px solid rgba(255, 255, 255, 0.1);
        padding: 3rem 0 2rem 0;
        background: #000000;
        color: #ffffff;
    }

    .footer-content {
        grid-column: span 12;
        display: grid;
        grid-template-columns: repeat(12, 1fr);
        gap: 2rem;
    }

    .footer-brand {
        grid-column: span 4;
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    .footer-brand h3 {
        font-size: 2rem;
        margin: 0;
    }

    .footer-brand p {
        color: rgba(255, 255, 255, 0.6);
        line-height: 1.6;
        margin: 0;
        font-size: 0.875rem;
    }

    .footer-nav {
        grid-column: span 4;
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    .footer-nav h4 {
        margin: 0 0 0.5rem 0;
        font-size: 0.875rem;
        text-transform: uppercase;
        letter-spacing: 0.05em;
        color: #f4a484;
    }

    .footer-nav ul {
        display: flex;
        flex-direction: column;
        gap: 0.75rem;
        list-style: none;
        padding: 0;
        margin: 0;
    }

    .footer-nav a {
        color: rgba(255, 255, 255, 0.7);
        text-decoration: none;
        transition: color 0.3s ease;
        font-size: 0.9rem;
    }

    .footer-nav a:hover {
        color: #f4a484;
    }

    .footer-social {
        grid-column: span 4;
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    .footer-social h4 {
        margin: 0 0 0.5rem 0;
        font-size: 0.875rem;
        text-transform: uppercase;
        letter-spacing: 0.05em;
        color: #f4a484;
    }

    .social-links {
        display: flex;
        gap: 1rem;
    }

    .social-links a {
        color: rgba(255, 255, 255, 0.7);
        transition: all 0.3s ease;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 40px;
        height: 40px;
        border: 1px solid rgba(255, 255, 255, 0.1);
    }

    .social-links a:hover {
        color: #f4a484;
        border-color: #f4a484;
        transform: translateY(-2px);
    }

    .footer-bottom {
        grid-column: span 12;
        padding-top: 2rem;
        margin-top: 2rem;
        border-top: 1px solid rgba(255, 255, 255, 0.1);
        display: flex;
        justify-content: space-between;
        align-items: center;
        font-size: 0.875rem;
        color: rgba(255, 255, 255, 0.5);
    }

    .footer-bottom a {
        color: rgba(255, 255, 255, 0.5);
        text-decoration: none;
        transition: color 0.3s ease;
    }

    .footer-bottom a:hover {
        color: #f4a484;
    }

    /* Tablet */
    @media (max-width: 1024px) {
        .footer-brand,
        .footer-nav,
        .footer-social {
            grid-column: span 6;
        }
    }

    /* Mobile */
    @media (max-width: 768px) {
        footer {
            padding: 2rem 0 1rem 0;
        }

        .footer-content {
            gap: 2rem;
        }

        .footer-brand,
        .footer-nav,
        .footer-social {
            grid-column: span 12;
        }

        .footer-brand h3 {
            font-size: 1.5rem;
        }

        .footer-bottom {
            flex-direction: column;
            gap: 1rem;
            text-align: center;
        }
    }
</style>

<footer>
    <Container>
        <div class="footer-content">
            <div class="footer-brand">
                <h3 class="morganite">CB DIGITAL</h3>
                <p>Building exceptional digital experiences that elevate brands and engage audiences.</p>
            </div>

            <div class="footer-nav">
                <h4>Navigation</h4>
                <ul>
                    {#each navigation as item}
                        <li>
                            <a href={item.link}>{item.name}</a>
                        </li>
                    {/each}
                </ul>
            </div>

            <div class="footer-social">
                <h4>Connect</h4>
                <div class="social-links">
                    {#each socials as social}
                        <a 
                            href={social.link} 
                            target="_blank" 
                            rel="noopener noreferrer"
                            aria-label={social.name}
                        >
                            {@html social.icon}
                        </a>
                    {/each}
                </div>
            </div>

            <div class="footer-bottom">
                <p>&copy; {currentYear} CB Digital. All rights reserved.</p>
                <p>
                    Designed & Built by CB Digital
                </p>
            </div>
        </div>
    </Container>
</footer>