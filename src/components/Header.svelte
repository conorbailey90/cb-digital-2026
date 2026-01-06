<script>
    import Container from "./Container.svelte";
    import { base } from "$app/paths";
    
    let isOpen = $state(false);

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

    const tabs = [
        {name: 'Home', link: `${base}/#home`},
        {name: 'About', link: `${base}/#about`},
        {name: 'Services', link: `${base}/#services`},
        {name: 'Projects', link: `${base}/#projects`},
        {name: 'Contact', link: `${base}/#contact`},
    ]

    function toggleMenu() {
        isOpen = !isOpen;
    }

    function closeMenu() {
        isOpen = false;
    }
</script>

<header>
    <Container>
        <div class="logo">
            <h3 class="morganite">CB DIGITAL</h3>
        </div>

        <!-- Desktop Navigation -->
        <nav class="desktop-nav">
            <ul>
                {#each tabs as tab}
                    <li>
                        <a href={tab.link}>{tab.name}</a>
                    </li>
                {/each}
            </ul>
        </nav>

        <!-- Mobile Hamburger Button -->
        <button class="hamburger" onclick={toggleMenu} aria-label="Toggle menu">
            <span class:open={isOpen}></span>
            <span class:open={isOpen}></span>
            <span class:open={isOpen}></span>
        </button>
    </Container>

    <!-- Mobile Menu Overlay -->
    <div class="mobile-menu" class:open={isOpen}>
        <nav class="mobile-nav">
            <ul>
                {#each tabs as tab}
                    <li>
                        <a href={tab.link} onclick={closeMenu}>{tab.name}</a>
                    </li>
                {/each}
            </ul>
        </nav>
        

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
</header>

<style>
    header {
        position: fixed;
        display: flex;
        justify-content: center;
        top: 0;
        left: 0;
        width: 100%;
        height: 60px;
        z-index: 100;
        overflow: visible;
    }

    .logo {
        align-self: center;
        grid-column: span 6;
    }

    .logo h3 {
        font-size: 2rem;
    }

    .desktop-nav {
        display: flex;
        align-items: center;
    }

    .desktop-nav ul {
        display: flex;
        list-style: none;
        padding: 0;
        margin: 0;
    }

    .desktop-nav a {
        margin-right: 0.5rem;
        align-self: center;
        text-decoration: none;
        transition: opacity 0.3s ease;
    }

    .desktop-nav a:hover {
        opacity: 0.7;
    }

    /* Hamburger Button */
    .hamburger {
        position: relative;
        top: -5px;
        display: none;
        flex-direction: column;
        justify-content: space-between;
        width: 30px;
        grid-column: 12;
        height: 16px;
        background: none;
        border: none;
        cursor: pointer;
        padding: 0;
        z-index: 101;
        align-self: center;
        justify-self: flex-end;
    }

    .hamburger span {
        display: block;
        width: 100%;
        height: 2px;
        background-color: currentColor;
        transition: all 0.3s ease;
        transform-origin: center;
    }

    .hamburger span.open:nth-child(1) {
        transform: translateY(7px) rotate(45deg);
    }

    .hamburger span.open:nth-child(2) {
        opacity: 0;
    }

    .hamburger span.open:nth-child(3) {
        transform: translateY(-7px) rotate(-45deg);
    }

    /* Mobile Menu */
    .mobile-menu {
        position: fixed;
        top: 0px;
        left: 0;
        width: 100%;
        height: calc(100vh);
        background-color: var(--bg-primary, #000000);
        z-index: 99;
        transform: translateX(-100px);
        opacity: 0;
        transition: transform 0.3s ease, opacity 0.3s ease;
        pointer-events: none;
    }

    .mobile-menu.open {
        transform: translateX(0);
        opacity: 1;
        pointer-events: all;
    }

      .social-links {
        width: calc(100vw - 4rem);
        border-top: 1px solid rgba(255, 255, 255, 0.279);
        position: relative;
        display: flex;
        gap: 1rem;
        margin-top: 1rem;
        padding-top: 1rem;
        left:2rem;
    
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

    .mobile-nav {
        padding: 2rem;
    }

    .mobile-nav ul {
        list-style: none;
        padding: 0;
        margin: 0;
        display: flex;
        flex-direction: column;
        gap: 1.5rem;
    }

    .mobile-nav a {
        font-size: 1.5rem;
        text-decoration: none;
        text-transform: uppercase;
        transition: opacity 0.3s ease;
        display: block;
    }

    .mobile-nav a:hover {
        opacity: 0.7;
    }

    /* Tablet and Mobile */
    @media (max-width: 768px) {
        .desktop-nav {
            display: none;
        }

        .hamburger {
            display: flex;
        }

    }

    @media (max-width: 480px) {


        .mobile-nav a {
            font-size: 1.25rem;
        }
    }
</style>