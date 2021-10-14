<template>
    <div class="project-card">
        <img v-bind:src="project.image" v-bind:alt="project.imageDesc" class="project-image" @click.prevent="openLink">
        <div class="card-text">
            <h3 class="card-title" @click.prevent="openLink">{{project.title}}</h3>
            <p class="card-p" @click.prevent="openLink">{{project.description}}</p> 
        </div>

    </div>
</template>

<script>
export default {
    name: 'ProjectCard',
    props: ["project"],
    methods: {
        openLink(){
            window.open(this.$props.project.link)
        }
    }
}
</script>

<style scoped>
    .project-card{
        position: relative;
        background: #07090D;
        border-radius: 15px;
        cursor: pointer;
        margin-bottom: 4rem;
    }

    .project-image{
        width: 300px;
        display: block;
        transition: opacity ease-out 0.3s;
        box-shadow: 2px 4px 16px #07090D;
    }

    img{
        border-radius: 15px;
    }

    .card-title{
        color: #469fec;
        margin-bottom: .5rem;
    }

    .card-title::after {
        content: '';
        width: 220px;
        height: 2px;
        display: block;
        position: absolute;
        margin-left: 23px;
        top: 1.5rem;
        background: #fff;
    }

    .card-p{
        color: white;
    }

    .project-card:hover > .project-image{
        opacity: 0.2;
    }
    
    .card-text{
        position: absolute;
        top: 20%;
        margin-left: 1.1em;
        margin-right: 1.1em;
        opacity: 0.0;
        transition: opacity ease-out 0.3s;
    }

    .project-card:hover > .card-text{
        opacity: 1;
    }

    @media screen and (max-width: 415px){
        .project-image{
            width: 275px;
        }

        .card-title::after {
            width: 200px;
            height: 2px;
            top: 1.5rem;
            left: 0px;
        }
    }

</style>