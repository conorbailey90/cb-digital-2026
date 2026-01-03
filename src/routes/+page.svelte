<script>
    import { onMount } from 'svelte';
    import Hero from "../components/Hero.svelte";
    import About from "../components/About.svelte";
    import Services from '../components/Services.svelte';

    // @ts-ignore
    let sections = [];
    
    onMount(() => {
          // @ts-ignore
        sections = document.querySelectorAll('section[data-bg-color]');
        
        const observer = new IntersectionObserver(
            (entries) => {
                entries.forEach((entry) => {
                    if (entry.isIntersecting) {
                        console.log(entry.target.getAttribute('data-bg-color'))
                        const bgColor = entry.target.getAttribute('data-bg-color');
                        if (bgColor) {
                            document.body.style.backgroundColor = bgColor;
                        }
                    }
                });
            },
            {
                threshold: 0.5 // Section needs to be 50% visible to trigger
            }
        );

        sections.forEach((section) => {
            observer.observe(section);
        });

        return () => {
              // @ts-ignore
            sections.forEach((section) => {
                observer.unobserve(section);
            });
        };
    });
</script>

<Hero />
<About />
<Services />

<style>
    :global(body) {
        transition: background-color 0.6s ease;
    }
</style>