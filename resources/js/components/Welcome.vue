<template>
    <div class="app">
        <!-- Container (About Section) -->
        <section class="vh-100" style="background-color: #eee;" v-if="!isLoginForm">
            <div class="container h-100">
                <div class="row d-flex justify-content-center align-items-center h-100">
                    <div class="col-lg-12 col-xl-11">
                        <div class="card text-black" style="border-radius: 25px;">
                            <div class="card-body p-md-5">
                                <div class="row justify-content-center">
                                    <div class="col-md-10 col-lg-6 col-xl-5 order-2 order-lg-1">

                                        <p class="text-center h1 fw-bold mb-5 mx-1 mx-md-4 mt-4">Sing In</p>

                                        <form class="mx-1 mx-md-4">

                                            <div class="d-flex flex-row align-items-center mb-4">
                                                <i class="fas fa-envelope fa-lg me-3 fa-fw"></i>
                                                <div class="form-outline flex-fill mb-0">
                                                    <input v-model="login.email" id="emailInput" type="email"  class="form-control" />
                                                    <label class="form-label" for="form3Example3c">Your Email</label>
                                                </div>
                                            </div>

                                            <div class="d-flex flex-row align-items-center mb-4">
                                                <i class="fas fa-lock fa-lg me-3 fa-fw"></i>
                                                <div class="form-outline flex-fill mb-0">
                                                    <input v-model="login.password" id="passwordInput" type="password" class="form-control" />
                                                    <label class="form-label" for="form3Example4c">Password</label>
                                                </div>
                                            </div>

                                            <div class="form-check d-flex justify-content-center mb-5">
                                                <label class="form-check-label" for="form2Example3">
                                                    Already have an account ? <a href="#!" @click = "toRegister" >Create an account</a>
                                                </label>
                                            </div>
                                            <div class="form-check d-flex justify-content-center mb-5" v-if="loginError">
                                                <label class="form-check-label" for="form2Example3">
                                                    <p style="color: red">{{loginError}}</p>
                                                </label>
                                            </div>

                                            <div class="d-flex justify-content-center mx-4 mb-3 mb-lg-4">
                                                <button type="button" @click="log()" class="btn btn-primary btn-lg">Login </button>
                                            </div>

                                        </form>

                                    </div>
                                    <div class="col-md-10 col-lg-6 col-xl-7 d-flex align-items-center order-1 order-lg-2">

                                        <img src="https://mdbcdn.b-cdn.net/img/Photos/new-templates/bootstrap-registration/draw1.webp"
                                             class="img-fluid" alt="Sample image">

                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class="vh-100" style="background-color: #eee;" v-if="isLoginForm">
            <div class="container h-100">
                <div class="row d-flex justify-content-center align-items-center h-100">
                    <div class="col-lg-12 col-xl-11">
                        <div class="card text-black" style="border-radius: 25px;">
                            <div class="card-body p-md-5">
                                <div class="row justify-content-center">
                                    <div class="col-md-10 col-lg-6 col-xl-5 order-2 order-lg-1">

                                        <p class="text-center h1 fw-bold mb-5 mx-1 mx-md-4 mt-4">Sign up</p>

                                        <form class="mx-1 mx-md-4">

                                            <div class="d-flex flex-row align-items-center mb-4">
                                                <i class="fas fa-user fa-lg me-3 fa-fw"></i>
                                                <div class="form-outline flex-fill mb-0">
                                                    <input  v-model="registration.name" id="regiNameInput" type="text" class="form-control" />
                                                    <label class="form-label" for="form3Example1c">Your Name</label>
                                                    <small id="emailHelp" class="form-text text-muted" v-if="registerError">{{registerError.name ? registerError.name[0] : ''}}</small>

                                                </div>
                                            </div>

                                            <div class="d-flex flex-row align-items-center mb-4">
                                                <i class="fas fa-envelope fa-lg me-3 fa-fw"></i>
                                                <div class="form-outline flex-fill mb-0">
                                                    <input v-model="registration.email" id="regiEmailInput" type="email"  class="form-control" />
                                                    <label class="form-label" for="form3Example3c">Your Email</label>
                                                    <small id="emailHelp" class="form-text text-muted" v-if="registerError">{{ registerError.email ? registerError.email[0] : ''}}</small>

                                                </div>
                                            </div>

                                            <div class="d-flex flex-row align-items-center mb-4">
                                                <i class="fas fa-lock fa-lg me-3 fa-fw"></i>
                                                <div class="form-outline flex-fill mb-0">
                                                    <input v-model="registration.password" id="RegiPassowrdInput" type="password" class="form-control" />
                                                    <label class="form-label" for="form3Example4c">Password</label>
                                                    <small id="emailHelp" class="form-text text-muted" v-if="registerError">{{ registerError.password ? registerError.password[0] : ''}}</small>
                                                </div>
                                            </div>

                                            <div class="d-flex flex-row align-items-center mb-4">
                                                <i class="fas fa-key fa-lg me-3 fa-fw"></i>
                                                <div class="form-outline flex-fill mb-0">
                                                    <input v-model="registration.password_confirmation" type="password" class="form-control" />
                                                    <label class="form-label" for="form3Example4cd">Repeat your password</label>
                                                </div>
                                            </div>

                                            <div class="form-check d-flex justify-content-center mb-5">
                                                <label class="form-check-label" for="form2Example3">
                                                    Already have an account ? <a href="#!" @click = "toLogin" >Sign In</a>
                                                </label>
                                            </div>

                                            <div class="d-flex justify-content-center mx-4 mb-3 mb-lg-4">
                                                <button type="button" class="btn btn-primary btn-lg" @click="register()">Register</button>
                                            </div>

                                        </form>

                                    </div>
                                    <div class="col-md-10 col-lg-6 col-xl-7 d-flex align-items-center order-1 order-lg-2">
                                        <img src="https://mdbcdn.b-cdn.net/img/Photos/new-templates/bootstrap-registration/draw1.webp"
                                             class="img-fluid" alt="Sample image">

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
    name:'Nav',
    data(){
        return{
            login:{
                email:'',
                password:'',
            },
            registration:{
                name:'',
                email:'',
                password:'',
                password_confirmation:''
            },
            registerError : {},
            currentRoute:'',
            user:'',
            isLog:false,
            reset:{
                email:'',
                password:'',
            },
            loginError:'',
            isLoginForm : false,


        }
    },
    mounted() {
        const user = JSON.parse(localStorage.getItem('user'));
        if(user) {
            this.isLog = true;
        }

    },
    created() {

    },
    methods:{
        toRegister(){
            this.isLoginForm = true;
            console.log(this.isLoginForm,'isLoginForm')
        },
        toLogin(){
            this.isLoginForm = false;
            console.log(this.isLoginForm,'isLoginForm')
        },
        log() {
            axios.post('/api/login', this.login
            ).then(response => {
                console.log("********", response.data.error);
                if (response.data.error) {
                    this.loginError =response.data.error;
                } else {
                    localStorage.setItem("user", JSON.stringify(response.data.user, response.data.token));
                    localStorage.setItem("token", JSON.stringify(response.data[0].token));
                    this.currentRoute = this.$router.currentRoute.name;
                    this.isLog = true;

                    this.$nextTick(() => {
                        if (this.isLog) {
                            this.$router.push({path: "/user-dashboard"});
                        }
                    });
                }
                this.login.email = '';
                this.login.password = '';

            });

        },
        register(){
            axios.post('/api/register',
                this.registration
            ).then(response => {
                if(response.data.errors){
                    this.registerError = response.data.errors;
                }
                else{
                    console.log(response.data,'jhcuda')
                    localStorage.setItem("user", JSON.stringify(response.data.user, response.data.token));
                    localStorage.setItem("token", JSON.stringify(response.data.token));
                    this.currentRoute = this.$router.currentRoute.name;
                    this.isLog = true;
                    this.$router.push({path: "/user-dashboard"});
                }
            });


        },
        logout(){
            localStorage.removeItem("user");
            localStorage.removeItem("token");
            this.$router.push({path: "/"});
            this.isLog = false;
            location.reload();
        },
        resetPassword(){
            axios.post('/api/reset-password',
                this.reset
            ).then(response => {
                console.log(response.data);
            });
            location.reload();
        }

    }

}
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
