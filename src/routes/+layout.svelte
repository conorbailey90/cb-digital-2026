<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import '../app.css';
	import SmoothScroll from '../components/SmoothScroll.svelte';
	import Header from '../components/Header.svelte';
	import Footer from '../components/Footer.svelte';
	let { children } = $props();

</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>
<SmoothScroll />
<main>
	<Header />
	{@render children()}
	<Footer />
</main>
