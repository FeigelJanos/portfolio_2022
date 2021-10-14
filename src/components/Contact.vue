<template>
    <section id="contact">
        <h2>Contact</h2>

        <p id="contact-par1">Feel free to contact me on any of the channels found here or in my CV.</p>
         
        <div id="direct-msg" :class="{
                'open': formVisible
              }"> 
            <button @click.prevent="toggleForm" id="msg-btn">
                <i class="fas fa-comment-alt" v-if="!formVisible"></i>
            <p :class="{
                'active': formVisible
              }">{{buttonMessage}}</p></button>

            <form @submit.prevent="submitForm" id="message-form" v-if="formVisible">
                <span id="top-error">{{errorMsg}}</span>

                <label for="email" id="mail-l">Email:</label>
                <input type="email" name="email" id="mail-i" v-model="email">

                <label for="message" id="msg-l">Message:</label>
                <textarea name="message" id="msg-i" cols="30" rows="10" v-model="message"></textarea>

                <button type="submit" id="send-btn">Send</button>
            </form>
        </div>   

        <div id="contacts">
            <a href="https://www.facebook.com/feigel.janos/" target="blank"><i class="fab fa-facebook-square"></i><p>Facebook</p></a>
            <a href="mailto:<nowiki> feigel_janos@yahoo.com?subject=Portfolio message"><i class="fas fa-envelope"></i><p>Email</p></a>
            <a href="https://www.linkedin.com/in/janos-feigel-dev" target="blank"><i class="fab fa-linkedin"></i><p>LinkedIn</p></a>
        </div>
    </section>
</template>

<script>
export default {
    name: 'Contact',
    data(){
        return {
                formVisible: false,
                email: '',
                message: '',
                errorMsg: '',
            }
    },
    methods: {
        toggleForm(){
            this.formVisible = !this.formVisible
        },
        async submitForm(){
            const inputsAreValid = this.validateInputs()

            this.formVisible = !this.formVisible
            console.log(inputsAreValid)
        },
        validateInputs(){
            return true
        }
    },
    computed: {
        buttonMessage(){
            if(this.formVisible){
                return "X"
            }
            return "Send a message"
        }
    }
}
</script>

<style scoped>
    h2{
        margin-bottom: 1.5rem;
        color: #469fec;
    }

    #direct-msg{
        margin-top: 1.5rem;
    }

    #contacts{
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
        margin-top: 1.5rem;
        margin-bottom: 1.5rem;
    }

    a{
        color: #469fec
    }

    a:visited{
        color: #469fec
    }

    #msg-btn{
        background-color: #0E121B;
        border: none;
        color: #f7b801;
        font-size: 1rem;
        font-family: 'Montserrat', sans-serif;
        font-weight: 900;
        cursor: pointer;
        margin-bottom: .5rem;
    }

    #message-form{
        margin: auto;
        width: 350px;
        display: grid;
        gap: 1rem;
        grid-template-areas:
                         "err err err"
                         "mail-l mail mail"
                         "... msg-l ..."
                         "msg msg msg"  
                         "... btn ... "
    }

    #mail-l{
        font-weight: bold;
        grid-area: mail-l;
    }

    #mail-i{
        grid-area: mail;
    }

    #msg-l{
        font-weight: bold;
        grid-area: msg-l;
    }

    #msg-i{
        grid-area: msg;
    }

    #send-btn{
        background-color: #469fec;
        border-color: #176DDE;
        border-radius: 15px;
        padding: .75rem;
        font-weight: bold;
        font-size: 1rem;
        grid-area:  btn;
        cursor: pointer;
        margin-bottom: 2.5rem;
        box-shadow: 2px 4px 16px black;
    }

    #send-btn:hover{
        background-color: #91C3F3;
        border-color: #469fec;
    }

    .active{
        padding-top: .5rem;
        font-size: 1.5rem;
        background-color: #39496A;
        color: #fff;
    }

    .open{
        margin: auto;
        background-color: #39496A;
        width: 400px;
        box-shadow: 2px 4px 16px black;
    }

    @media screen and (max-width: 415px){
        #message-form{
            grid-template-areas:
                         "err err err"
                         "mail-l mail-l mail-l"
                         "mail  mail mail"
                         "msg-l msg-l msg-l"
                         "msg msg msg"  
                         "... btn ... "
        }

        #direct-msg{
            width: 350px;
            margin: auto;
        }

        #mail-i{
            width: 300px;
            margin: auto;
        }

        #msg-i{
            width: 300px;
            margin: auto;
        }

        #contact > p{
            margin-bottom: 1rem;
        }

        #send-btn{
            width: 140px;
        }
    }

</style>