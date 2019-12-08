<template>
    <div id="login" class="d-flex justify-content-center">
        <div class="container" style="margin-top: 100px;">
            <div class="row d-flex justify-content-center">
                <div class ="col-md-4 col-md-offset-4">
                    <div class="panel panel-default">
                        <h4>Login With</h4><br>
                        <span><i class="fa fa-facebook"></i></span>
                        <span><i class="fa fa-twitter"></i></span>
                        <span><i class="fa fa-google-plus"></i></span>
                        <br><br>
                        <h4>OR</h4><hr>
                        <div class="panel-body">
                            <form action="">
                                <div class="form-group">
                                    <input id = "stuff" type="text" class = "form-control" name="username" placeholder="Username" v-model="input.username">
                                </div>
                                <div class="form-group">
                                    <input type="password" class = "form-control" name="password" placeholder="Password" v-model="input.password">
                                </div>
                                <div class="form-group row">

                                    <div class="col-md-6">
                                        <div class="form-check">
                                            <label class="form-check-label">
                                                <input class="form-check-input" type="checkbox"> Remember Me
                                            </label>
                                        </div>
                                    </div>
                                </div>
                                <div class="form-group">

                                    <button class="btn btn-primary btn-success btn-lg btn-block"  v-on:click="login()">
                                        Login
                                        <i class="fa fa-sign-in"></i>
                                    </button>
                                </div>

                            </form>
                        </div>
                    </div><!--Panel Default-->
                </div><!--Col-->
            </div><!--Row-->
        </div><!--Container-->
    </div>
</template>

<script>
    import json from '../assets/User.json'
    export default {
        name: "Login",
        data() {
            return {
                userdata: json,
                input: {
                    username: "",
                    password: ""
                }
            }
        },
        methods: {
            login(){this.$emit("authenticated", true);
                if(this.input.username != "" && this.input.password != "") {
                    for(let i = 0; i<this.userdata.length ;i++){
                        if(this.input.username == this.userdata[i].id && this.input.password == this.userdata[i].password) {
                            this.$emit("authenticated", true);
                            break;
                        }

                    }

                }
            }
        }
    }
</script>

<style scoped>

.panel{
    border: 0px;
    background: rgba(0,0,0,0.5);
    color: #fff;
    text-align: center;
    padding-top: 80px;
    padding-bottom: 30px;
    padding-left: 20px;
    padding-right: 20px;
    transition: 1s;
    border-radius: 40px;
    box-shadow: 10px 10px 10px rgba(0,0,0,1);
}

.fa-facebook{
    color: #3B5998
}
.fa-twitter{
    color: #1DA1F2
}
.fa-google-plus{
    color: red;
}

.panel:hover {
    background: rgba(0,0,0,0.7);
}

span{
    width: 40px;
    height: 40px;
    line-height: 40px;
    display: inline-block;
    background: #fff;
    text-align: center;
    border-radius: 4px;
    margin-left: 10px;
    -webkit-box-shadow: -10px 10px 10px rgba(0,0,0,0.5);
    box-shadow: -10px 10px 10px rgba(0,0,0,0.5);
    transition: 1s;
}
span:hover{
    background: rgba(0,255,255,1);
}

h4{
    margin: 0;
    padding: 0;
    color: #fff;
    }
</style>