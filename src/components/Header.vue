<template>
    <header id="header"  @mouseleave.prevent="closeMenu">
        <button class="hamburger hamburger--3dx" :class="{
                'is-active': burgerIsActive
              }" type="button" @click.prevent="toggleHamburger" id="burger-btn">
            <span class="hamburger-box">
                <span class="hamburger-inner"></span>
            </span>
        </button>
        <transition name="fade">
        <nav v-if="burgerIsActive" id="menu" >
            <ul id="link-list">
                <a href="#hello"> <li>Home</li></a> 
                <a href="#about"><li> About </li></a>
                <a href="#technologies"><li> Technologies </li></a>
                <a href="#projects"><li> Projects </li></a>
                <a href="#contact"><li> Contact </li></a>
            </ul>
        </nav>
        </transition>
    </header>
</template>

<script>
export default {
    name: "HeaderBar",
    data(){
        return {
            burgerIsActive: false
        }
    },
    methods: {
        toggleHamburger(){
            this.burgerIsActive = !this.burgerIsActive
        },
        closeMenu(){
            if(this.burgerIsActive){
                this.burgerIsActive = !this.burgerIsActive
            }
        }
    }
}
</script>

<style scoped>
    #header{
        position: relative;
    }

    #burger-btn{
        margin-left: 1rem;
        float: left;
    }
    #menu{
        position: absolute;
        top: 3rem;
        left: 2rem;
        background-color: #469fec
    }

    #link-list{
        list-style: none;
        text-decoration: none;
        color: #0E121B;
    }

    #link-list li{
        padding: 1rem;
        width: 250px;
        cursor: pointer;
        border-top:  2px solid #0E121B;
    }

    #link-list a li{
        color: #0E121B;
        font-weight: bold;
    }

    #link-list li:hover {
        background-color: #91C3F3;
    }

    #link-list a li:visited{
        color: #0E121B;
    }

    .fade-enter-from {
        opacity: 0;
    }

    .fade-enter-active {
        transition: all 0.2s linear;
    }
        
    .fade-leave-active {
        transition: all 0.2s linear;
        opacity: 0;
        position: absolute;
    }
</style>