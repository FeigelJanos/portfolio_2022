<template>
<div>
  <header-bar />

  <div id="hello">
    <h1 >Hey! I am John.</h1>
    <h2>A web developer</h2>
  </div>


  <about />

  <technologies />

  <projects />

  <contact />

  <footer-bar />
</div>
</template>

<script>
import Projects from './components/Projects.vue'
import Contact from './components/Contact.vue'
import About from './components/About.vue'
import Technologies from './components/Technologies.vue'
import FooterBar from './components/Footer.vue'
import HeaderBar from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Projects,
    Contact,
    About,
    Technologies,
    HeaderBar,
    FooterBar
  }
}
</script>

<style>
*{
  box-sizing: border-box;
  line-height: 1.5;
  font-weight: 300;
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Work Sans', sans-serif;
  color: white;
  background-color: #0E121B;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

#hello{
  padding-top: 4rem;
  margin-bottom: 4rem;
}

h1, h2, h3 {
  font-family: 'Montserrat', sans-serif;
  font-weight: 900;
}

#hello h2{
  font-style: italic;
  color: #F7B801;
}

#profile-pic{
  width: 200px;
  border-radius: 50%;
}

a{
  cursor: pointer;
  text-decoration: none;
}

</style>
