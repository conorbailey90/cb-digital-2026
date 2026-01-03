<script>
       import Container from "./Container.svelte";
       import ServiceAccordian from "./ServiceAccordian.svelte";
</script>

<section data-bg-color="#000000">

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
        width: 100%
    }

    .line{
        height: 1px;
        width: 100%;
        background-color: white;
        grid-column: span 12;
    }

    h2{
        grid-column: span 5;
        text-transform: uppercase;
    }
</style>