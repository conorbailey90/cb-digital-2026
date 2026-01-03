<script lang="ts">
	let { children } = $props();
</script>


<div class="container">
    {@render children()}
</div>

<style>
    .container{
        display: grid;
        width: 95%;
        grid-template-columns: repeat(12, 1fr);
        gap: .5rem;
    }
</style>