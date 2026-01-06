<script>
       import Container from "./Container.svelte";
       import ServiceAccordian from "./ServiceAccordian.svelte";
</script>

<section id="services" data-bg-color="#000000" data-text-color="#FFFFFF">

    <Container>
        <h4>Services</h4>
        <div class="line"></div>
        <h2>Bringing together strategy, creativity, and technology to craft visual products and campaigns that thrive across all platforms internationally</h2>
        <ServiceAccordian />
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

    h4 {
        grid-column: span 12;
    }

    .line {
        grid-column: span 12;
        height: 1px;
     
        margin-bottom: 2rem;
    }

    h2 {
        grid-column: span 5;
        text-transform: uppercase;
        line-height: 1.3;
        margin-bottom: 2rem;
    }

    /* Tablet */
    @media (max-width: 1024px) {
        section {
            padding-top: 60px;
        }

        h2 {
            grid-column: span 7;
            font-size: 1.5rem;
        }

        .line {
            margin-bottom: 1.5rem;
        }
    }

    /* Mobile */
    @media (max-width: 768px) {
        section {
            padding-top: 4rem;
        }

        h4 {
            font-size: 1.25rem;
            margin-bottom: 1rem;
        }

        h2 {
            grid-column: span 12;
            font-size: 1.2rem;
            line-height: 1.4;
            margin-bottom: 1.5rem;
        }

        .line {
            margin-bottom: 1.5rem;
        }
    }

    /* Small Mobile */
    @media (max-width: 480px) {
        section {
            padding-top: 3rem;
        }

        h4 {
            font-size: 1.1rem;
        }

        h2 {
            font-size: 1rem;
            line-height: 1.5;
        }
    }
</style>