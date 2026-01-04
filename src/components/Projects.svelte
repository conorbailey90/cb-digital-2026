<script>
	import Container from "./Container.svelte";
    import { base } from "$app/paths";

    const projects = [
        {
            title: 'BRICKLAYING & PLASTERING COURSES',
            services: [
                'Design',
                'Development',
                'Content Management System',
                'Database'
            ],
            image: 'bpc-mockup.avif',
            link: 'https://baileys-construction-academy-m8ca.vercel.app/'
        },
        {
            title: 'FACEWORX',
            services: [
                'Design',
                'Development',
                'Content Management System',
                'Database'
            ],
            image: 'fw-mockup.avif',
            link: 'https://www.faceworx.beauty/'
        },
        {
            title: 'AXIONET',
             services: [
                'Design',
                'Development',
                'Educational / Tutorial'
            ],
            image: 'axios-mockup.avif',
            link: 'https://www.youtube.com/watch?v=Fb0MCsdGGZ8&t=8s'
        },
    ]
</script>

<section id="projects" data-bg-color="#000000" data-text-color="#FFFFFF">
    <Container>
        <div class="header">
            <h4>Projects</h4>
        </div>
        <div class="line"></div>
        
        <div class="projects-grid">
            {#each projects as project, i}
                <article class="project-card">
                    <a href={project.link} target="_blank" rel="noopener noreferrer" class="project-link">
                        <div class="image-wrapper">
                            <div class="image-container">
                                <img src="{base}/images/{project.image}" alt="{project.title}">
                            </div>
                            <div class="overlay">
                                <span class="view-project">View Project →</span>
                            </div>
                        </div>
                        <div class="content">
                            <div class="project-number">0{i + 1}</div>
                            <h3 class="project-title">{project.title}</h3>
                            <div class="services-list">
                                {#each project.services as service}
                                    <span class="service-item">{service}</span>
                                {/each}
                            </div>
                        </div>
                    </a>
                </article>
            {/each}
        </div>
    </Container>
</section>

<style>
    section {
        display: flex;
        justify-content: center;
        padding: 80px 0 2rem 0;
    }

    .header {
        display: flex;
      
        grid-column: span 12;
 
    }
    
    .projects-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
        gap: .5rem;
        grid-column: span 12;
    }

    .project-card {
        position: relative;
    }

    .project-link {
        display: block;
        text-decoration: none;
        color: white;
        height: 100%;
    }

    .image-wrapper {
        position: relative;
        aspect-ratio: 16 / 10;
        overflow: hidden;
        background: rgba(255, 255, 255, 0.02);
        border: 1px solid rgba(255, 255, 255, 0.1);
        margin-bottom: 1.5rem;
    }

    .image-container {
        width: 100%;
        height: 100%;
        transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .image-container img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        display: block;
    }

    .overlay {
        position: absolute;
        inset: 0;
        background: linear-gradient(to top, rgba(0, 0, 0, 0.8), transparent 50%);
        display: flex;
        align-items: flex-end;
        justify-content: center;
        padding: 2rem;
        opacity: 0;
        transition: opacity 0.4s ease;
    }

    .view-project {
        font-size: 1rem;
        font-weight: 500;
        color: white;
        transform: translateY(20px);
        transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .project-link:hover .image-container {
        transform: scale(1.05);
    }

    .project-link:hover .overlay {
        opacity: 1;
    }

    .project-link:hover .view-project {
        transform: translateY(0);
    }

    .content {
        padding: 0 0.5rem;
    }

    .project-number {
        font-size: 0.875rem;
        color: rgba(255, 255, 255, 0.4);
        margin-bottom: 0.75rem;
        font-weight: 300;
    }

    .project-title {
        font-size: 1.25rem;
        font-weight: 500;
        margin: 0 0 1.25rem 0;
        line-height: 1.3;
        letter-spacing: -0.02em;
    }

    .services-list {
        display: flex;
        flex-wrap: wrap;
        gap: 0.5rem;
    }

    .service-item {
        font-size: 0.8rem;
        color: rgba(255, 255, 255, 0.6);
        padding: 0.4rem 0.9rem;
        border: 1px solid rgba(255, 255, 255, 0.15);
        transition: all 0.3s ease;
    }

    .project-link:hover .service-item {
        color: rgba(255, 255, 255, 0.9);
        border-color: rgba(255, 255, 255, 0.3);
    }

    /* Tablet */
    @media (max-width: 1024px) {
        .projects-grid {
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: .5rem;
        }
        .project-card{
            margin-bottom: 1rem;
        }
    }

    /* Mobile */
    @media (max-width: 768px) {
        section {
            padding: 4rem 0;
        }

        .header {
            flex-direction: column;
            align-items: flex-start;
            gap: 1rem;
        }

        .projects-grid {
            grid-template-columns: 1fr;
            gap: 3rem;
        }

        .project-title {
            font-size: 1.1rem;
        
        }
    }
</style>