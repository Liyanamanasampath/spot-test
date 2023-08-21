<template>
    <div>

        <section class="vh-100" style="background-color: #9de2ff;">
            <div class="container py-5 h-100">
                <div class="row d-flex justify-content-center align-items-center h-100">
                    <div class="col col-md-9 col-lg-7 col-xl-5">
                        <div class="card" style="border-radius: 15px;">
                            <div class="card-body p-4">
                                <div class="d-flex text-black">
                                    <div class="flex-shrink-0">
                                        <img src="https://mdbcdn.b-cdn.net/img/Photos/new-templates/bootstrap-profiles/avatar-1.webp"
                                             alt="Generic placeholder image" class="img-fluid"
                                             style="width: 180px; border-radius: 10px;">
                                    </div>
                                    <div class="flex-grow-1 ms-3">
                                        <h5 class="mb-1">{{user.name}}</h5>
                                        <p class="mb-2 pb-1" style="color: #2b2a2a;">{{user.email}}</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

    </div>
</template>

<script>
export default {
    data() {
        return {
            user : ''
        };
    },
    async created() {
        this.user = JSON.parse(localStorage.getItem('user'));
        if(this.user) {
            this.isLog = true;
        }
    },
    methods: {

    }
};
</script>

<style  scoped>
h2 {
    font-size: 24px;
    text-transform: uppercase;
    color: #303030;
    font-weight: 600;
    margin-bottom: 30px;
    font-family: lato;
}
h4 {
    font-size: 19px;
    line-height: 1.375em;
    color: #303030;
    font-weight: 400;
    margin-bottom: 30px;
    font-family:tess;
}
.jumbotron {
    background-color: #343A40;
    color: #fff;
    padding: 100px 25px;
    font-family: Montserrat, sans-serif;
}
</style>
