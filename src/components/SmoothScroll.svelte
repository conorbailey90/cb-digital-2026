<script>
  import { onMount } from 'svelte';
  import Lenis from 'lenis';

    /**
	 * @type {Lenis}
    */
  let lenis;

  onMount(() => {
    // Initialize Lenis
    lenis = new Lenis({
    //   duration: 1.2,
    //   easing: (t) => Math.min(1, 1.001 - Math.pow(2, -10 * t)),
      orientation: 'vertical',
      smoothWheel: true,
      wheelMultiplier: 1,
      touchMultiplier: 2,
      infinite: false,
    });

    // Animation frame loop
    /**
	   * @param {number} time
	*/
    function raf(time) {
      lenis.raf(time);
      requestAnimationFrame(raf);
    }

    requestAnimationFrame(raf);

    // Cleanup
    return () => {
      lenis.destroy();
    };
  });
</script>