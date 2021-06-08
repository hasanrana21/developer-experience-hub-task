<template>
    <div class="home-page">
        <Header/>
    </div>
</template>

<script>
import Header from "../Header/Header";
export default {
    data(){
        return {
            // data return here
        }
    },
    components: {
        'Header': Header,
    }
}
</script>

<style>
    .home-page{
        width: 100%;
        height:100vh;
    }
</style>