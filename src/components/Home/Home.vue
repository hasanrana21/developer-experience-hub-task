<template>
    <div class="home-page">
        <Header/>
        <!-- <Modal/> -->
    </div>
</template>

<script>
import Header from "../Header/Header";
// import Modal from "../Modal/Modal";
export default {
    data(){
        return {
            // data return here
        }
    },
    components: {
        'Header': Header,
        // 'Modal': Modal,
    }
}
</script>

<style>
    .home-page{
        width: 100%;
        height:100vh;
    }
</style>