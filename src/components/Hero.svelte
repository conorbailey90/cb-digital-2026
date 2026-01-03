<script>
// @ts-nocheck

    import { onMount } from 'svelte';
    import Container from "./Container.svelte";
     import { base } from '$app/paths';

    let images = [
        '/images/axios-mockup.png',
        '/images/bpc-mockup.png',
        '/images/fw-mockup.png'
    ];

    let image;

    let ukTime = $state(new Intl.DateTimeFormat('en-GB', {
        timeZone: 'Europe/London',
        hour: '2-digit',
        minute: '2-digit',
        hour12: false
    }).format(new Date()));

    let currentImageIndex = $state(0);

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

        // Cycle images every 5 seconds
        // const imageInterval = setInterval(() => {
        //     // Step 1: Fade out current image
        //     image.style.opacity = '0';
            
        //     // Step 2: After fade out completes, change the image source
        //     setTimeout(() => {
        //         currentImageIndex = (currentImageIndex + 1) % images.length;
                
        //         // Step 3: Immediately after changing source, fade back in
        //         setTimeout(() => {
        //             image.style.opacity = '1';
        //         }, 50); // Small delay to ensure the image src has updated
        //     }, 500); // Wait for the fade out transition (matches CSS transition)
        // }, 5000);

        // Cleanup on unmount
        return () => {
            clearInterval(timeInterval);
            // clearInterval(imageInterval);
        };
    });
</script>

<section data-bg-color="#000000">
    <Container>
        <div class="intro">
            <h1 style="font-size: 5rem;" class="morganite">CB DIGITAL</h1><br/>
            <h3>Elevate Your Business <br />with Sleek, Modern Web Design</h3><br/>
            <p>We create clean, fast, and mobile-friendly websites with reliable hosting solutions, designed to showcase your small business with clarity and style, effortlessly attracting and engaging your customers.</p><br/>

            <div style="display: flex;">
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
        width: 100%
    }

    .intro{
        grid-column: span 5;
        margin: 1rem 0 2rem 0;
    }

    .intro h1 {
        background: linear-gradient(135deg, #ffffff 0%, #ffffff 50%, #fcfcfc 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
    }

    .intro h3 {
       text-transform: uppercase;
    }
  
    .dot{
        position: relative;
        width: 5px;
        height: 5px;
        background-color: white;
        border-radius: 50%;
        animation: flash infinite linear 2s;
        align-self: center;
        margin: 0 .5rem;
    }

    .projects_preview{
        left: -5%;
        width: 110%;
        position: relative;
        grid-column: span 12;
        height: 400px;
        /* aspect-ratio: 16 / 16; */
    }

    img{
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: opacity 0.5s ease-in-out;
    }

    @keyframes flash{
        0% {
            opacity: 0%;
        }

        50%{
            opacity: 100%;
        }

        100%{
            opacity: 0%;
        }
    }
</style>