<script>
    import { onMount } from 'svelte';
    import Hero from "../components/Hero.svelte";
    import About from "../components/About.svelte";
    import Services from '../components/Services.svelte';
    import Projects from '../components/Projects.svelte';
    import Prices from '../components/Prices.svelte';
	import Contact from '../components/Contact.svelte';
</script>

<Hero />
<About />
<Services />
<Projects />
<Prices />
<Contact />

<style>
    :global(body) {
        transition: background-color 0.6s ease;
    }
</style>