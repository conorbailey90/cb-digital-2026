<script>
	import { onMount } from "svelte";
    import Container from "./Container.svelte";

    const aboutSections = [
        {
            title: 'Bespoke websites designed <br> to elevate your business.',
            text: 'CB Digital specialises in clean, minimal web design that communicates clearly and looks sharp on every device. Each website is purpose-built — no templates, no clutter — just custom design that reflects your brand and delivers a smooth, engaging user experience.'
        },
        {
            title: 'Modern development <br> with performance in mind.',
            text: 'Every site is built using best-in-class tools and frameworks to ensure fast load times, responsive layouts, and long-term maintainability. Whether it\'s a simple brochure site or a more complex solution, development is handled with precision to ensure performance, accessibility, and SEO readiness from day one.'
        },
        {
            title: 'Fully managed hosting <br> and ongoing support.',
            text: 'CB Digital offers reliable, secure hosting options with technical support and site maintenance included. From setup to launch and beyond, everything is handled to keep your website running smoothly — including updates, backups, and performance monitoring — so you can focus on your business.'
        },
    ]

   
</script>

<section data-bg-color="#FF0000">

    <Container>

        <h4>About</h4>
        <div class="line"></div>

        {#each aboutSections as section}
            <div class="sticky_container">
                <div class="about_item">
                    <div class="section_title">
                        <h3>{@html section.title}</h3>
                    </div>
                    <div class="section_text">
                        <p>{section.text}</p>
                    </div>
                </div>
                
            </div>
        {/each}

    </Container>

</section>

<style>
    section{
        margin: 2rem 0;
        display: flex;
        justify-content: center;
    }
    .line{
        height: 1px;
        width: 100%;
        background-color: white;
        grid-column: span 12;
    }

    .sticky_container{
        position: sticky;
        min-height: 50vh;
        grid-column: span 12;
    }

    .about_item{
        position: sticky;
        top: 80px;
        display: grid;
        grid-template-columns: repeat(12, 1fr);
    }

   

    .section_title{
        padding-right: 2rem;
        grid-column: span 6;
    }
    .section_title h3{
        text-transform: uppercase;
        font-size: 1.5rem;
        text-wrap: balance;
    }

    .section_text{
        grid-column: span 5;
    }
</style>