<template>
    <div id="fancy-modal">
        <button class="login-button" @click="showModal = true">Login</button>

        <transition name="fade" appear>
            <div class="modal-overlay" v-if="showModal" @click="showModal = false"></div>
        </transition>

        <transition name="slide" appear>
            <div id="modal" v-if="showModal">
                <div class="text-end">
                    <button class="cross-button" @click="showModal = false">X</button>
                </div>

                <form v-on:submit.prevent  @submit="logInFormSubmit()" @click="submitedButton = false">
                    <div class="mb-3">
                        <label for="exampleInputEmail1" class="form-label">Email address</label>
                        <input type="email" name="email" @change="handleInput()" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
                    </div>
                    <div class="mb-3">
                        <label for="exampleInputPassword1" class="form-label">Password</label>
                        <input type="password" name="password" @change="handleInput()" class="form-control" id="exampleInputPassword1">
                    </div>
                    <div class="text-center" @click="submitedButton = true"  >
                        <button type="submit" class="btn btn-primary" v-if="submitedButton"  id="submit-button">Submit</button>
                    </div>
                </form>
            </div>
        </transition>
    </div>
</template>

<script>
export default {
    data(){
        return{
            //data return here
            showModal: true,
            submitedButton: true,
            handleInput(){

            },

        }
    },
    methods: {
            logInFormSubmit(){
                console.log("form submited");
            },
    }
}
</script>

<style scoped>
    #fancy-modal{
        position: relative;
        display: flex;
        justify-content: flex-end;
        width: 100%;
        height: 100vh;
        overflow-x: hidden;
    }

    .login-button{
        border: none;
        padding: 10px 25px;
        border-radius: 5px;
        background-color:crimson;
        color: white;
        font-size: 18px;
        font-weight: 700;
        width: 100px;
        height: 50px;
        margin-right: 40px;
        margin-top: 15px;
    }

    .modal-overlay{
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: 62;
        background-color: rgba(0, 0, 0, .5);
    }

    #modal{
        position: fixed;
        right: 0;
        z-index: 99;
        
        width: 100%;
        height: 100vh;
        max-width: 400px;
        background-color: #22272e;
        color: white;
        border-radius: 4px;
        
        padding: 30px;
        animation-name: hasan;

    }

    .cross-button{
        border: none;
        font-size: 21px;
        font-weight: 700;
        color: red;
        padding: 0 10px;
        border-radius: 4px;
        margin-bottom: 35px;
    }

    form label{
        color: whitesmoke;
    }


    .fade-enter-active,
    .fade-leave-active{
        transition: opacity 0.5s;
    }

    .fade-enter,
    .fade-leave-to{
        opacity: 0;
    }

    .slide-enter-active,
    .slide-leave-active {
    transition: transform .6s;
    }

    .slide-enter,
    .slide-leave-to {
    transform: translateY(0%) translateX(100vw);
    }


    #submit-button{
        animation-name: submited;
        transition: 3s;
    }

    @keyframes submited {
        0%{
            height: 50px;
            width: 200px;
        }
        25%{
            height: 50px;
            width: 150px;
            margin-top: 30px;
        }
        50%{
            height: 50px;
            width: 120px;
            border-radius: 50%;
            margin-top: 50px;
        }
        75%{
            height: 50px;
            width: 100px;
            margin-top: 70px;
        }
        100%{
            height: 50px;
            width: 50px;
            border-radius: 50%;
            margin-top: 100px;
        }
    }
</style>