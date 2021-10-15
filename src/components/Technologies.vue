<template>
<section id="technologies">
    <h2>Technologies</h2>

    <p>I am interested in all aspects of web development. I love spending time on fixing little details and optimizing the code. 
    I also like working in a team, and consider teamwork and knowledge sharing essential parts of a good work environment. </p>

    <p>I belive that in programming, to fully comprehend new knowledge it have to be used in practice. 
    I wite code every day and allways have at least one work in progress project that exceeds my current abilities.</p>

    <div id="technology-cards">
        <technology-card v-for="card in cards" :key="card.title" :card="card"/>
    </div>
</section>   
</template>


<script>
import TechnologyCard from './TechnologyCard.vue'

export default {
    name: 'Technologies',
    components: {
        TechnologyCard
    },
    data(){
        return {
            cards: [
                {
                    title: 'Front End Development',
                    description: 'I like to bring new ideas to life in the browser.',
                    technologies: ["HTML", "CSS", "JS", "Vue"]
                },
                            {
                    title: 'Back End Development',
                    description: 'I like to use Node JS to create scalable and fast applications.',
                    technologies: ["TS", "JS", "Node JS", "Express", "Nest"]
                },
                            {
                    title: 'Databases',
                    description: 'I like to utilise both SQL and No SQL databases to optimize performance.',
                    technologies: ["Mongo DB", "Postgre SQL", "Oracle", "Elasticsearch" ]
                }
            ]
        }
    }
}
</script>

<style scoped>
    #technologies{
        margin-left: 2rem;
        margin-right: 2rem;
    }

    h2{
        margin-bottom: 1.5rem;
        color: #469fec;
    }

    #technology-cards{
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        margin-top: 2rem;
    }
</style>