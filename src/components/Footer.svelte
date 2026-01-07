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
            name: 'Instagram',
            link: 'https://www.instagram.com/cbdgtl/',
            icon: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 256 256"><path d="M128,80a48,48,0,1,0,48,48A48.05,48.05,0,0,0,128,80Zm0,80a32,32,0,1,1,32-32A32,32,0,0,1,128,160ZM176,24H80A56.06,56.06,0,0,0,24,80v96a56.06,56.06,0,0,0,56,56h96a56.06,56.06,0,0,0,56-56V80A56.06,56.06,0,0,0,176,24Zm40,152a40,40,0,0,1-40,40H80a40,40,0,0,1-40-40V80A40,40,0,0,1,80,40h96a40,40,0,0,1,40,40ZM192,76a12,12,0,1,1-12-12A12,12,0,0,1,192,76Z"></path></svg>'
        },
        {
            name: 'Facebook',
            link: 'https://facebook.com',
            icon: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 256 256"><path d="M128,24A104,104,0,1,0,232,128,104.11,104.11,0,0,0,128,24Zm8,191.63V152h24a8,8,0,0,0,0-16H136V112a16,16,0,0,1,16-16h16a8,8,0,0,0,0-16H152a32,32,0,0,0-32,32v24H96a8,8,0,0,0,0,16h24v63.63a88,88,0,1,1,16,0Z"></path></svg>'
        },
        {
            name: 'YouTube',
            link: 'https://www.youtube.com/c/conorbailey',
            icon: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" viewBox="0 0 256 256"><path d="M164.44,121.34l-48-32A8,8,0,0,0,104,96v64a8,8,0,0,0,12.44,6.66l48-32a8,8,0,0,0,0-13.32ZM120,145.05V111l25.58,17ZM234.33,69.52a24,24,0,0,0-14.49-16.4C185.56,39.88,131,40,128,40s-57.56-.12-91.84,13.12a24,24,0,0,0-14.49,16.4C19.08,79.5,16,97.74,16,128s3.08,48.5,5.67,58.48a24,24,0,0,0,14.49,16.41C69,215.56,120.4,216,127.34,216h1.32c6.94,0,58.37-.44,91.18-13.11a24,24,0,0,0,14.49-16.41c2.59-10,5.67-28.22,5.67-58.48S236.92,79.5,234.33,69.52Zm-15.49,113a8,8,0,0,1-4.77,5.49c-31.65,12.22-85.48,12-86,12H128c-.54,0-54.33.2-86-12a8,8,0,0,1-4.77-5.49C34.8,173.39,32,156.57,32,128s2.8-45.39,5.16-54.47A8,8,0,0,1,41.93,68c30.52-11.79,81.66-12,85.85-12h.27c.54,0,54.38-.18,86,12a8,8,0,0,1,4.77,5.49C221.2,82.61,224,99.43,224,128S221.2,173.39,218.84,182.47Z"></path></svg>'
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
        font-size: 4rem;
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
            font-size: 3rem;
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