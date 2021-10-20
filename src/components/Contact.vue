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
                <textarea name="message" id="msg-i" cols="30" rows="10" v-model="message" maxlength="2000"></textarea>

                <button type="submit" id="send-btn" :disabled="sumbitted">{{sendBtnText}}</button>
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
                submitted: false,
                email: '',
                message: '',
                errorMsg: '',
                sendBtnText: 'Send',
            }
    },
    methods: {
        toggleForm(){
            this.formVisible = !this.formVisible

            if(!this.formVisible && this.errorMsg.length > 0){
                this.errorMsg = '';
            }
        },
        async submitForm(){
            const inputsAreValid = this.validateInputs()

            if(!inputsAreValid){
                return
            }

            const response = await fetch('https://feigel-apis.com', {
                method: 'POST',
                credentials: 'omit',
                cache: 'no-cache',
                mode: 'cors',
                headers: {
                    'Content-Type': 'application/json',
                    'Access-Control-Allow-Origin':'https://feigel-apis.com'
                },
                redirect: 'follow',
                referrerPolicy: 'no-referrer',
                body: JSON.stringify({ id: '0002', email: this.email, message: this.message})
            }).catch(()=>{
                this.errorMsg= 'The message was not delivered. Please try again later.'
            })

            console.log(response)
            if(response.status !== 200){
                 this.errorMsg= 'The message was not delivered. Please try again later.'
            }
            else{
                this.sumbitted = true;
                this.sendBtnText= 'Message sent'
                this.errorMsg = '';
                this.email= '';
                this.message= '';
            }
        },
        validateInputs(){
            if(this.email.length < 1 ){
                this.errorMsg = "You must fill in your email."
                return false
            }

            if(this.message.length < 1 ){
                this.errorMsg = "You must write some message."
                return false
            }
            /*eslint-disable */
            const emailRegex = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
            /*eslint-enable */

            if(emailRegex.test(this.email)){
                this.errorMsg=''
                return true
            }

            this.errorMsg = 'Email format is invalid.'
            return false
            
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
        margin-top: 4rem;
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
        margin-bottom: 1rem;
        margin-top: .5rem;
        margin-left: 1.5rem;
        margin-right: 1.5rem;
    }

    #message-form{
        margin: auto;
        width: 350px;
        display: grid;
        gap: 1rem;
        text-align: center;
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

    #send-btn:disabled{
        background-color: #999999;
        border-color: #666666;
    }

    #send-btn:disabled:hover{
        background-color: #999999;
        border-color: #666666;
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
        text-align: right;
    }

    #top-error{
        grid-area: err;
        color: red;
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

        @media screen and (min-width: 1018px) {

        #contacts{
            width: 1018px;
            margin: auto;
        }

        #contacts a{
            margin-top: 2rem;
            margin-bottom: 2rem;
        }

         #contact p{
             font-size: 1.1rem;
         }

        #contact i{
             font-size: 1.1rem;
         }

        #contact h2{
             font-size: 1.6rem;
         }
        
    }

</style>