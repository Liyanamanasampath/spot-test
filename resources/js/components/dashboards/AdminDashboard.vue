<template>
    <div class="container">
        <div class="row">
             <div class="col-sm-12 text-center mb-5 mt-5">
        <h1>
           welcome  {{user[0].name}}
        </h1>
             </div>
        </div>
    </div>
</template>

<script>
import { openDB } from "idb";

export default {
    data() {
        return {
            models: {
                email: "",
                first_name: "",
                last_name: ""
            },
            user : ''
        };
    },
    async created() {
         this.user = JSON.parse(localStorage.getItem('user'));
        console.log(this.user,'user')
        if(user) {
            this.isLog = true;
        }
    },
    methods: {

    }
};
</script>

<style scoped></style>
