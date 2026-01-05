<script>
    import Container from "./Container.svelte";
    import { base } from "$app/paths";
    const tabs = [
        {name: 'Home', link: `${base}/#home`},
        {name: 'About', link: `${base}/#about`},
        {name: 'Services', link: `${base}/#services`},
        {name: 'Projects', link: `${base}/#projects`},
    ]
</script>

<style>

    header{
        position: fixed;
        display: flex;
        justify-content: center;
        top: 0;
        left: 0;
        width: 100%;
        height: 60px;
        z-index: 1;
      
    }

    .logo{
        align-self: center;
        grid-column: span 6;
    }

    nav{
        display: flex;
        align-items: center;
    }

    ul{
        display: flex;
    }
  

    a{
        margin-right: .5rem;
        align-self: center;
    }
</style>

<header>
    <Container>
        <div class="logo">
            <h3 style="font-size: 2rem;" class="morganite">CB DIGITAL</h3>
        </div>
        <nav>
            <ul>
                {#each tabs as tab}
                    <li>
                        <a href={tab.link}>{tab.name}</a>
                    </li>
                {/each}
            </ul>
        </nav>
      
    </Container>
</header>


