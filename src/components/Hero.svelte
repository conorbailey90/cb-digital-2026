<script>
// @ts-nocheck

    import { onMount } from 'svelte';
    import Container from "./Container.svelte";
    import { base } from '$app/paths';

    let image;

    let ukTime = $state(new Intl.DateTimeFormat('en-GB', {
        timeZone: 'Europe/London',
        hour: '2-digit',
        minute: '2-digit',
        hour12: false
    }).format(new Date()));


    onMount(() => {
        image = document.querySelector('.projects_preview > img')

        // Update time every 60 seconds (HH:MM)
        const timeInterval = setInterval(() => {
            ukTime = new Intl.DateTimeFormat('en-GB', {
                timeZone: 'Europe/London',
                hour: '2-digit',
                minute: '2-digit',
                hour12: false
            }).format(new Date());
        }, 60000);

       
        // Cleanup on unmount
        return () => {
            clearInterval(timeInterval);
            // clearInterval(imageInterval);
        };
    });
</script>

<section id="home" data-bg-color="#000000" data-text-color="#FFFFFF">
    <Container>
        <div class="intro">
            <h1 class="morganite">CB DIGITAL</h1><br/>
            <h3>Elevate Your Business <br />with Sleek, Modern Web Design</h3><br/>
            <p>We create clean, fast, and mobile-friendly websites with reliable hosting solutions, designed to showcase your small business with clarity and style, effortlessly attracting and engaging your customers.</p><br/>

            <div class="location-time">
                <p>London / Essex, UK</p><div class="dot"></div><p>{ukTime}</p>
            </div>
        </div>       

        <div class="projects_preview">
            <img src="{base}/images/Hero.avif" alt="..." />
        </div>
    </Container>
</section>

<style>
    section {
        display: flex;
        padding-top: 80px;
        justify-content: center;
        position: relative;
        width: 100%;
    }

    .intro {
        grid-column: span 5;
        margin: 1rem 0 2rem 0;
    }

    .intro h1 {
        font-size: 5rem;
        background: linear-gradient(135deg, #ffffff 0%, #ffffff 50%, #fcfcfc 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
    }

    .intro h3 {
       text-transform: uppercase;
    }
  
    .location-time {
        display: flex;
        align-items: center;
    }

    .dot {
        position: relative;
        width: 5px;
        height: 5px;
        background-color: white;
        border-radius: 50%;
        animation: flash infinite linear 2s;
        align-self: center;
        margin: 0 .5rem;
    }

    .projects_preview {
        left: -5%;
        width: 110%;
        position: relative;
        grid-column: span 12;
        height: 400px;
    }

    img {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: opacity 0.5s ease-in-out;
    }

    @keyframes flash {
        0% {
            opacity: 0%;
        }

        50% {
            opacity: 100%;
        }

        100% {
            opacity: 0%;
        }
    }

    /* Tablet */
    @media (max-width: 1024px) {
        section {
            padding-top: 60px;
        }

        .intro {
            grid-column: span 6;
        }

        .intro h1 {
            font-size: 3.5rem;
        }

        .intro h3 {
            font-size: 1.25rem;
        }

        .intro p {
            font-size: 0.95rem;
        }

        .projects_preview {
            height: 350px;
        }
    }

    /* Mobile */
    @media (max-width: 768px) {
        section {
            padding-top: 80px;
        }

        .intro {
            grid-column: span 12;
            margin: 1rem 0 1.5rem 0;
        }

        .intro h1 {
            font-size: 2.5rem;
            line-height: 1.1;
        }

        .intro h3 {
            font-size: 1.1rem;
            line-height: 1.3;
        }

        .intro h3 br {
            display: none;
        }

        .intro p {
            font-size: 0.9rem;
            line-height: 1.6;
        }

        .location-time {
            flex-wrap: wrap;
            gap: 0.25rem;
        }

        .location-time p {
            font-size: 0.85rem;
        }

        .projects_preview {
            left: 0;
            width: 100%;
            height: 300px;
            margin-top: 1rem;
        }
    }

    /* Small Mobile */
    @media (max-width: 480px) {
        section {
            padding-top: 70px;
        }

        .intro h1 {
            font-size: 2rem;
        }

        .intro h3 {
            font-size: 1rem;
        }

        .intro p {
            font-size: 0.85rem;
        }

        .location-time p {
            font-size: 0.8rem;
        }

        .projects_preview {
            height: 250px;
        }
    }
</style>