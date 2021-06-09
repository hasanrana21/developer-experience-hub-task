<template>
    <div id="fancy-modal">
        <button class="login-button" @click="showModal = true">Login</button>

        <transition name="fade" appear>
            <div class="modal-overlay" v-if="showModal" @click="showModal = false"></div>
        </transition>

        <transition name="slide" appear>
            <div class="modalClass" v-if="showModal">
                <div class="text-end">
                    <button class="cross-button" @click="showModal = false || firstSlide()">X</button>
                </div>

                <form v-on:submit.prevent>
                    <div id="inputs" v-if="submitedButton">
                        <div class="mb-3">
                            <label for="exampleInputEmail1" class="form-label">Email address</label>
                            <input type="email" name="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
                        </div>

                        <div class="mb-3">
                            <label for="exampleInputPassword1" class="form-label">Password</label>
                            <input type="password" name="password" class="form-control" id="exampleInputPassword1">
                        </div>
                    </div>
                    
                    <div class="text-center sendDiv" @click="submitedButton = false">
                        <button type="submit" class="btn btn-primary" @click="dataSubmit = true" id="submit-button">Submit</button>                              
                    </div> 
                </form>
        
                <transition name="secondSlide" appear>
                    <div class="slideAfterSlide"  v-if="dataSubmit" @click="dataSubmit = true"></div>
                </transition> 
            </div>

        </transition>

        <transition name="anotherDiv" appear>
            <div class="slideAfterClick"  v-if="dataSubmit" @click="dataSubmit = true"> </div>
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
            show: true,
            dataSubmit: false,
        }
    },
    methods: {
        firstSlide(){
            this.dataSubmit = false;
        }
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

    .modalClass{
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
        
    }
    .modalClass input{
        max-width: 325px;
    }
    .slideAfterClick{
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: 80;
        background-color: #22272e;
        max-width: 100%;
    }
    .slideAfterSlide{
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: 99;
        background-color: lightgrey;
        width: 100%;
        margin-right: -30%;
        margin-left: 15%;
        margin-top: 10%;
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
/* end */
    .slide-enter-active,
    .slide-leave-active {
    transition: transform .6s;
    }

    .slide-enter,
    .slide-leave-to {
    transform: translateY(0%) translateX(100vw);
    }
/* end */

    .anotherDiv-enter-active,
    .anotherDiv-leave-active {
    transition: transform .6s;
    }

    .anotherDiv-enter,
    .anotherDiv-leave-to {
    transform: translateY(0%) translateX(100vw);
    }
/* end */
    .secondSlide-enter-active,
    .secondSlide-leave-active {
    transition: transform .6s;
    }

    .secondSlide-enter,
    .secondSlide-leave-to {
    transform: translateY(0%) translateX(200vw);
    }
</style>