<template>
    <div class="app">
        <Nav
            :isLog="isLog"
        />
        <h1>App vue</h1>

        <router-view></router-view>
    </div>
</template>

<script>

import Nav from './Nav'

export default {
    name: "App",
    data(){
        return{
            user:'',
            isLog:false,
        }
    },
    components: {
        Nav
    },
    mounted() {
        this.user = JSON.parse(localStorage.getItem('user'));
        if (this.user !== '') {
            this.isLog = true;
        } else {
            this.isLog = false;
        }
    }
}
</script>

<style  scoped>

</style>
