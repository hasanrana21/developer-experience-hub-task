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
                <h2>Hasan Rana</h2>
                <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Nam eum dolores asperiores reiciendis in vero enim placeat quo aliquam nemo.</p>
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
        }
    },
    methods: {
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
        /* cursor: pointer; */
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
        
        padding: 25px;
        animation-name: hasan;

    }

    .cross-button{
        border: none;
        font-size: 21px;
        font-weight: 700;
        color: red;
        padding: 0 10px;
        border-radius: 4px;
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
</style>