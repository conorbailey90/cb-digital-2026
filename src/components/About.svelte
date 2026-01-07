<script>
	import { onMount } from "svelte";
    import Container from "./Container.svelte";
    import { base } from '$app/paths';
    import { reveal } from '$lib/actions/reveal';

    const aboutSections = [
        {
            title: 'Bespoke websites designed <br> to elevate your business.',
            text: 'CB Digital specialises in clean, minimal web design that communicates clearly and looks sharp on every device. Each website is purpose-built — no templates, no clutter — just custom design that reflects your brand and delivers a smooth, engaging user experience.',
              img: '/images/ebp.gif'
        },
        {
            title: 'Modern development <br> with performance in mind.',
            text: 'Every site is built using best-in-class tools and frameworks to ensure fast load times, responsive layouts, and long-term maintainability. Whether it\'s a simple brochure site or a more complex solution, development is handled with precision to ensure performance, accessibility, and SEO readiness from day one.',
              img: '/images/faceworx.gif'
        },
        {
            title: 'Fully managed hosting <br> and ongoing support.',
            text: 'CB Digital offers reliable, secure hosting options with technical support and site maintenance included. From setup to launch and beyond, everything is handled to keep your website running smoothly — including updates, backups, and performance monitoring — so you can focus on your business.',
            img: '/images/omg1.avif'
        },
    ]

    // @ts-ignore
    let canvas;
    // @ts-ignore
    let ctx;
    // @ts-ignore
    let animationId;

    onMount(() => {
        canvas = document.getElementById('gridCanvas');
        // @ts-ignore
        ctx = canvas.getContext('2d');
        
        const resizeCanvas = () => {
            // @ts-ignore
            canvas.width = canvas.offsetWidth;
            // @ts-ignore
            canvas.height = canvas.offsetHeight;
        };

        resizeCanvas();
        window.addEventListener('resize', resizeCanvas);

        const squareSize = 50;
        const gap = 1;
        // @ts-ignore
        let blobX = canvas.width / 2;
        // @ts-ignore
        let blobY = canvas.height / 2;
        let blobVelX = 2;
        let blobVelY = 1.5;
        const blobRadius = 150;

        const animate = () => {
            // Clear canvas
            // @ts-ignore
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // Update blob position
            blobX += blobVelX;
            blobY += blobVelY;

            // Bounce blob off edges and constrain position
            // @ts-ignore
            if (blobX + blobRadius > canvas.width) {
                // @ts-ignore
                blobX = canvas.width - blobRadius;
                blobVelX *= -1;
            }
            if (blobX - blobRadius < 0) {
                blobX = blobRadius;
                blobVelX *= -1;
            }
            // @ts-ignore
            if (blobY + blobRadius > canvas.height) {
                // @ts-ignore
                blobY = canvas.height - blobRadius;
                blobVelY *= -1;
            }
            if (blobY - blobRadius < 0) {
                blobY = blobRadius;
                blobVelY *= -1;
            }

            // Draw golden blob with blur
            // @ts-ignore
            const gradient = ctx.createRadialGradient(blobX, blobY, 0, blobX, blobY, blobRadius);
            gradient.addColorStop(0, 'rgba(218, 165, 32, 0.8)');
            gradient.addColorStop(0.5, 'rgba(218, 165, 32, 0.4)');
            gradient.addColorStop(1, 'rgba(218, 165, 32, 0)');
            
            // @ts-ignore
            ctx.filter = 'blur(20px)';
            // @ts-ignore
            ctx.fillStyle = gradient;
            // @ts-ignore
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            // @ts-ignore
            ctx.filter = 'none';

            // Draw grid of black squares
            // @ts-ignore
            const cols = Math.ceil(canvas.width / (squareSize + gap));
            // @ts-ignore
            const rows = Math.ceil(canvas.height / (squareSize + gap));

            // @ts-ignore
            ctx.fillStyle = '#000000';
            for (let row = 0; row < rows; row++) {
                for (let col = 0; col < cols; col++) {
                    const x = col * (squareSize + gap);
                    const y = row * (squareSize + gap);
                    // @ts-ignore
                    ctx.fillRect(x, y, squareSize, squareSize);
                }
            }

            animationId = requestAnimationFrame(animate);
        };

        animate();

        return () => {
            window.removeEventListener('resize', resizeCanvas);
            // @ts-ignore
            cancelAnimationFrame(animationId);
        };
    });
</script>

<section id="about" data-bg-color="#FFFFFF" data-text-color="#161616">
    <canvas id="gridCanvas"></canvas>

    <Container>

        <h4>About</h4>
        <div class="line"></div>

        {#each aboutSections as section}
            <div use:reveal class="about_container">
                <div class="about_item">
                    <div class="section_title">
                        <h3>{@html section.title}</h3>
                    </div>
                    <div class="section_text">
                        <p>{section.text}</p>
                        {#if section.img}
                            <div class="image_container">
                                <img src="{base}{section.img}" alt="">
                            </div>
                        {/if}
                     
                    </div>
                </div>
                
            </div>
        {/each}

    </Container>

</section>

<style>
    section {
        position: relative;
        margin: 2rem 0;
        padding: 80px 0 2rem 0;
        display: flex;
        justify-content: center;
    }

    #gridCanvas {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 0;
        pointer-events: none;
    }

    h4 {
        grid-column: span 12;
        position: relative;
        z-index: 1;
    }

    .line {
        grid-column: span 12;
        height: 1px;
        margin-bottom: 2rem;
        position: relative;
        z-index: 1;
    }

    .about_container {
        position: relative;
        grid-column: span 12;
        padding-bottom: 4rem;
        z-index: 1;
    }

    .about_item {
        display: grid;
        grid-template-columns: repeat(12, 1fr);
        gap: 2rem;
    }

    .section_title {
        padding-right: 2rem;
        grid-column: span 6;
    }

    .section_title h3 {
        text-transform: uppercase;
        font-size: 1.5rem;
        text-wrap: balance;
        line-height: 1.3;
    }

    .section_text {
        position: relative;
        grid-column: span 5;
    }

    .section_text p {
        line-height: 1.6;
    }

    .image_container {
        position: relative;
        margin-top: 1rem;
        width: 100%;
        aspect-ratio: 1 / .6;
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        border: 1px solid rgba(22, 22, 22, 0.1);
    }

    img {
        width: 100%;
    }

    /* Tablet */
    @media (max-width: 1024px) {
        section {
            padding: 80px 0 2rem 0;
        }

        .about_container {
            padding-bottom: 2rem;
        }

        .about_item {
            gap: 1.5rem;
        }

        .section_title {
            grid-column: span 7;
            padding-right: 1rem;
        }

        .section_title h3 {
            font-size: 1.3rem;
        }

        .section_text {
            grid-column: span 5;
        }

        .section_text p {
            font-size: 0.95rem;
        }

        .image_container {
            margin-top: 1.5rem;
        }
    }

    /* Mobile */
    @media (max-width: 568px) {
        section {
            margin: 1rem 0;
            padding: 4rem 0 1rem 0;
        }

        h4 {
            font-size: 1.25rem;
            margin-bottom: 1rem;
        }

        .line {
            margin-bottom: 1.5rem;
        }

        .about_container {
            margin-bottom: 2rem;
            padding-bottom: 0;
        }

        .about_item {
            grid-template-columns: 1fr;
            gap: 1.5rem;
        }

        .section_title {
            grid-column: span 1;
            padding-right: 0;
        }

        .section_title h3 {
            font-size: 1.2rem;
            line-height: 1.4;
        }

        .section_title h3 :global(br) {
            display: none;
        }

        .section_text {
            grid-column: span 1;
        }

        .section_text p {
            font-size: 0.9rem;
            line-height: 1.7;
        }

        .image_container {
            margin-top: 1.5rem;
        }
    }

    /* Small Mobile */
    @media (max-width: 480px) {
        section {
            padding: 3rem 0 1rem 0;
        }

        h4 {
            font-size: 1.1rem;
        }

        .about_container {
            margin-bottom: 2rem;
        }

        .section_title h3 {
            font-size: 1rem;
        }

        .section_text p {
            font-size: 0.85rem;
        }

        .image_container {
            margin-top: 1rem;
        }
    }
</style>