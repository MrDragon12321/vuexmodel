<template>
  <div class="sign">
    <div class="sign_card">
      <div style="text-align:center">
        <div class="inputDiv">
          <i class="el-icon-user"></i>
          <el-input
            placeholder="请输入账号"
            v-model.trim="username"
            @keyup.13='toHome'
          ></el-input>
        </div>
        <div class="inputDiv">
          <i class="el-icon-lock"></i>
          <el-input
            placeholder="请输入密码"
            type="password"
            v-model.trim="password"
            @keyup.enter='toHome'
          ></el-input>
        </div>
        <el-button @click="toRegister">跳转注册</el-button>
        <el-button @click="toHome">登录首页</el-button>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: '',
    }
  },
  methods: {
    toRegister() {
      this.$router.push("/register")
    },
    toHome() {
      this.$router.push("/home")
      this.$store.dispatch('addUserInfo', { "userName": this.username, "password": this.password })
    }
  }
}
</script>

<style lang="less">
.sign {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  .sign_card {
    width: 90rem;
    height: 55rem;
    box-shadow: 0 0 2rem gray;
    display: flex;
    justify-content: center;
    align-items: center;
    .inputDiv {
      position: relative;
      margin: 2rem 0;
      i {
        width: 2.2rem;
        height: 2.2rem;
        position: absolute;
        top: 1.3rem;
        left: 0.5rem;
        font-size: 1.6rem;
        z-index: 999;
      }
      .el-input {
        width: 25rem;
        .el-input__inner {
          padding: 0 1rem 0 3rem;
        }
      }
    }
  }
}
</style>