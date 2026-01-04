<script>
  import { onMount } from 'svelte';
  import Lenis from 'lenis';

  let { children } = $props();

  /**
   * @type {Lenis | null}
   */
  let lenis = null;

  onMount(() => {
    lenis = new Lenis({
      orientation: 'vertical',
      smoothWheel: true,
      wheelMultiplier: 1,
      touchMultiplier: 2,
      infinite: false,
    });

    let rafId;

    /**
     * @param {number} time
     */
    function raf(time) {
      lenis.raf(time);
      rafId = requestAnimationFrame(raf);
    }

    rafId = requestAnimationFrame(raf);

    return () => {
      if (rafId) cancelAnimationFrame(rafId);
      if (lenis) lenis.destroy();
    };
  });
</script>

{@render children()}