<template>
    <div class="technology-card">
        <h3>{{card.title}}</h3>

        <p>{{card.description}}</p>

    <div class="tech-list">
        <p>Technologies I often use:</p>
        <ul id="tech-items">
            <li v-for="element in card.technologies" :key="element">{{element}}</li>
        </ul>
    </div>

    </div>
</template>

<script>
export default {
    name: 'TechnologyCard',
    props: ["card"]
}
</script>

<style scoped>
.technology-card{
        background-color: #39496A;
        border-radius: 15px;
        color: #fff;
        width: 350px;
        padding: 1.5rem;
        position: relative;
        margin-bottom: 4rem;
        box-shadow: 2px 4px 16px black;
}

h3{
    margin-bottom: 1rem;
}

h3::after{
    content: '';
    width: 260px;
    height: 2px;
    display: block;
    position: absolute;
    margin-left: 20px;
    top: 3rem;
    background: #469fec;
}

.tech-list{
    margin-top: 1rem;
}

.tech-list p{
    font-weight: bold;
    margin-bottom: .5rem;
}

#tech-items{
    list-style-type: none;
}

@media screen and (max-width: 415px){
    h3::after{

    width: 260px;
    height: 2px;
    top: 3rem;
    left: 0px;
    background: #566E9F;
}
}
</style>