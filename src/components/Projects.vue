<template>
<section id="projects">
    <h2>Latest projects:</h2>

    <p>I created several projects, from small algorithms to more comprehensive applications. 
	Here are a few projects I've worked on recently.</p>
    
    <div id="project-cards">
        <project-card v-for="project in projects" :key="project.title" :project="project"/>
    </div>   
    </section>
</template>

<script>
import ProjectCard from './ProjectCard.vue'

export default {
    name: 'Projects',
    components: {
        ProjectCard
    },
    data(){
        return {
            projects: [
                {
                    title: "Wizards Game",
                    image: require("../assets/V2.png"),
                    imageDesc: "Wizards game page picture",
                    link: "https://feigeljanos.github.io/Wizards-Game",
                    description: "Small browser game made with vanilla JS"
                },
                {
                    title: "Previous Portfolio",
                    image: require("../assets/old-portfolio.png"),
                    imageDesc: "Previous portfolio page picture",
                    link: "https://feigeljanos.github.io/Personal-Page",
                    description: "Previous portfolio site made with vanilla JS"
                },
                {
                    title: "Arboriculture Site",
                    image: require("../assets/feigeladam.png"),
                    imageDesc: "Arboriculture site page picture",
                    link: "https://feigeladam.hu",
                    description: "Site made for an arboriculturist using Vue and an Express based email API"
                }
            ]
        }
    }
}
</script>

<style scoped>
    #projects{
        margin-left: 2rem;
        margin-right: 2rem;
        margin-bottom: 4rem;
    }

    h2{
        margin-bottom: 1.5rem;
        color: #469fec;
    }

    #project-cards{
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        background-color: #39496A;
        color: #0E121B;
        margin-top: 1.5rem;
        border-radius: 15px;
        padding-top: 4rem;
        box-shadow: 2px 4px 16px black;
    }

    @media screen and (min-width: 1018px) {

       #project-cards{
            width: 1018px;
            margin: auto;
        }

        #projects > p{
            margin-bottom: 4rem;
            font-size: 1.1rem;
        }

        #projects > h2{
            font-size: 1.6rem;
        }
        
    }
</style>