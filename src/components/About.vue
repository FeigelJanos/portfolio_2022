<template>
    <section id="about">
        <h2>About</h2>

        <p>I am an allround web developer with good knowledge of back-end techniques. 
        I love structure and order and I also stand for quality. 
        I try my best to create great user experience
        with performant and well designed apps and websites. 
        And to keep up with the newest techniques and tools in development.</p>
        
        <div id="short-info">
            <img id="profile-pic" src="..\assets\CV_Picture.jpg" alt="Profile picture">

            <div id="about-bar">
                <div id="location">
                    <h3>Location: </h3> 
                </div>
                <p>Hungary</p>

                <div id="code-sites">
                    <h3>Code samples:</h3>
                    <a href="https://github.com/FeigelJanos" target="blank">
                        <i class="fab fa-github-square"></i>
                    </a>  
                    <a href="https://codepen.io/JFeigel/pens/showcase" target="blank">
                        <i class="fab fa-codepen"></i>
                    </a>
                </div> 
            </div>

        </div> 

        <a href="/Feigel_Janos_CV_ENG.pdf"  download class="dl-link">
            <i class="fas fa-file-download"></i>
        </a>
        <div>
            <a href="/Feigel_Janos_CV_ENG.pdf" download class="dl-link">
                <p>Download my CV</p>
            </a>
        </div>

        
    </section>

</template>

<script>
export default {
    name: 'About'
}
</script>

<style scoped>
    #about{
        margin-left: 2rem;
        margin-right: 2rem;
        margin-bottom: 3rem;
    }

    h2{
        color: #469fec;
        margin-bottom: 1.5rem;
    }

    a{
        color: #469fec;
    }

    a:visited{
        color: #469fec;
    }

    #profile-pic{
    border-radius: 50%;
    shape-outside: circle(50%);
    margin-right: 2rem;
    margin-left: 2rem;
    box-shadow: 3px 3px 10px #000;
    }

    #about-bar{
        margin-right: 2rem;
        margin-left: 2rem;
    }

    #short-info{
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        margin-top: 2rem;
    }

    .dl-link i{
        margin-top: 3rem;
        color: #f7b801;
        font-size: 1.5rem;
    }

     .dl-link p{
         display: inline-block;
         color: #f7b801;
         font-family: 'Montserrat', sans-serif;
         font-weight: bold;
     }

    #code-sites i{
        font-size: 1.5rem;
        margin: .5rem;
    }
    #code-sites i:hover{
        color: #91C3F3;
    }

    #code-sites h3{
        margin-top: 1.5rem;
    }
</style>