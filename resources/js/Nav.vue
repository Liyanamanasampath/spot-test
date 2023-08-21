<template>
    <div class="app">
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top" role="navigation">

                <a class="navbar-brand text-left" href="/user-dashboard">Dashboard</a>
<!--            <div class="container">-->
                <button class="navbar-toggler border-0" type="button" data-toggle="collapse" data-target="#exCollapsingNavbar">
                    &#9776;
                </button>
                <div class="collapse navbar-collapse" id="exCollapsingNavbar">
                    <ul v-if="!isLog" class="nav navbar-nav flex-row text-right align-content-end">
                        <li class="nav-item order-2 order-md-1"><a href="#" class="nav-link" title="settings"><i class="fa fa-cog fa-fw fa-lg"></i></a></li>
                    </ul>
                    <ul class="nav navbar-nav flex-row justify-content-between ml-auto" v-if="isLog">
                        <li class="nav-item order-2 order-md-1"><a href="#" class="nav-link" title="settings"><i class="fa fa-cog fa-fw fa-lg"></i></a></li>
                        <li class="dropdown order-1">
                            <button type="button" id="dropdownMenu" data-toggle="dropdown" class="btn btn-outline-secondary dropdown-toggle" @click="logout()">Logout <span class="caret"></span></button>
                        </li>
                        <li class="dropdown order-1">
                            <button type="button" id="dropdownMenu" class="btn btn-outline-secondary " @click="viewProfile()">My Profile</button>
                        </li>
                    </ul>
                </div>
<!--            </div>-->
        </nav>

        <div id="modalPassword" class="modal fade" tabindex="-1" role="dialog" aria-labelledby="myModalLabel" aria-hidden="true">
            <div class="modal-dialog">
                <div class="modal-content">
                    <div class="modal-header">
                        <h3>Forgot password</h3>
                        <button type="button" class="close font-weight-light" data-dismiss="modal" aria-hidden="true">×</button>
                    </div>
                    <div class="modal-body">
                        <p>Reset your password..</p>
                        <form class="form" role="form">
                            <div class="form-group">
                                <input v-model="reset.email" id="resetEmailInput" placeholder="Email" class="form-control form-control-sm" type="email" required="">
                                <p class="text-warning small">* Previously used email address</p>
                            </div>
                            <div class="form-group">
                                <input v-model="reset.password" id="resetPasswordInput" placeholder="New Password" class="form-control form-control-sm" type="password" required="">
                            </div>
                        </form>
                    </div>
                    <div class="modal-footer">
                        <pre>{{test}}</pre>
                        <button class="btn" data-dismiss="modal" aria-hidden="true">Close</button>
                        <button class="btn btn-primary" @click="resetPassword()">Save changes</button>
                    </div>
                </div>
            </div>
        </div>



    </div>
</template>

<script>
export default {
    name:'Nav',
    props:['isLog'],
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
            currentRoute:'',
            user:'',
            reset:{
                email:'',
                password:'',
            },
            loginError:'',
            test: false



        }
    },
    mounted() {
        this.user = JSON.parse(localStorage.getItem('user'));
    },
    created() {

    },
    methods:{
        viewProfile() {
            this.$router.push({path: "/user-profile"});
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
                    this.$router.push({path: "/user-dashboard"});
                    this.currentRoute = this.$router.currentRoute.name;
                    this.isLog = true;
                }
                this.login.email = '';
                this.login.password = '';

            });

        },
        register(){
            axios.post('/api/register',
                this.registration
            ).then(response => {
                console.log(response.data);
            });
            location.reload();
            this.$router.push({path: "/"});

        },
        logout(){
            localStorage.removeItem("user");
            localStorage.removeItem("token");
            this.$router.push({path: "/"});
            this.isLog = false;
            location.reload();
            this.$emit()
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

button:focus {
    outline: 0;
}

.navbar .dropdown-menu .form-control {
    width: 200px;
}

</style>
