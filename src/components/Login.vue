
<template>
<body id="poster">
  <el-form class="login-container" label-position="left"
           label-width="0px">
    <!-- <h3 class="login_title">系统登录</h3> -->
    <img class="login_title" src="../assets/logo.png">
    <el-form-item>
      <el-input type="text" v-model="loginForm.username"
                auto-complete="off" placeholder="账号"></el-input>
    </el-form-item>
    <el-form-item>
      <el-input type="password" v-model="loginForm.password"
                auto-complete="off" placeholder="密码"></el-input>
                 
    </el-form-item>
   <el-link class="losspwd" v-model="loginForm.losspwd" type="info">忘记密码</el-link>
    <el-form-item style="width: 100%">
      <el-button type="primary" style="width: 100%;background: #505458;border: none" v-on:click="login">登录</el-button>
    </el-form-item>
    <el-button class ="guest" type="info" round >访客登录</el-button>
  </el-form>
</body>
</template>


<style>
  .login-container {
    position: absolute;
    border-radius: 15px;
    background-clip: padding-box;
    /* margin: 90px auto; */
    margin: 20% 50% 0% 40%;
    width: 350px;
    padding: 35px 35px 15px 35px;
    background: #fff;
    border: 1px solid #eaeaea;
    box-shadow: 0 0 25px #cac6c6;
  }
  
  .login_title {
     width: 100px;
    height: 100px;
  }

  .losspwd {
    margin: 1px 0px 20px 250px;
    text-align: center;
  }

  .guest {
    position: fixed;
    text-align: center;
    margin: -33% 0 100% 47% ;
    background: rgba(255, 255, 255, 0.01);
  }

  #poster {
      background:url("../assets/1.jpg") no-repeat;
      background-position: center;
      height: 100%;
      width: 100%;
      background-size: cover;
      position: fixed;
    }
    body{
      margin: 0px;
    }
    
    .mask{
        height:100%;
        width:100%;
        background: rgba(0,0,0,.4);
    }

</style>


<script>
export default {
  name: "Login",
  data() {
    return {
      loginForm: {
        username: "",
        password: ""
      },
      responseResult: []
    };
  },
  methods: {
    login() {
      this.$axios
        .post("/login", {
          username: this.loginForm.username,
          password: this.loginForm.password
        })
        .then(successResponse => {
          if (successResponse.data.code === 200) {
            this.$router.replace({ path: "/index" });
          }
        })
        .catch(failResponse => {});
    }
  }
};
</script>
