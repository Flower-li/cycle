<template>
  <div class="Login">
    <div class="nav" ref="forHeight">
      <el-row>
        <el-col :span="24">
          <el-link
            :underline="false"
            href="https://element.eleme.io"
            target="_blank"
            >关于我们</el-link
          >
          <el-link :underline="false" type="primary">注册1</el-link>
          <el-link :underline="false" type="success">忘记密码</el-link>
          <el-link :underline="false" type="warning">在线客服</el-link>
          <el-link :underline="false" type="danger">帮助中心</el-link>
          <el-link :underline="false" type="info"
            >联系电话：13906988092</el-link
          >
        </el-col>
      </el-row>
    </div>
    <div class="main" :style="{ height: mainHeight + 'px' }">
      <el-row>
        <el-col
          :span="6"
          :offset="17"
          :style="{ height: mainHeight + 'px' }"
          class="main-list"
        >
          <ul>
            <p>欢迎登陆</p>
            <span>用户账号</span>
            <el-input
              placeholder="请输入账号"
              prefix-icon="el-icon-user-solid"
              v-model="userName"
            >
            </el-input>
            <span>登陆密码</span>
            <el-input
              placeholder="请输入密码"
              prefix-icon="el-icon-s-goods"
              v-model="userPsw"
            >
            </el-input>
            <el-button type="warning" @click="login">登陆</el-button>
          </ul>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Login",
  components: {},
  data() {
    return {
      mainHeight: "",
      userName: "",
      userPsw: ""
    };
  },
  mounted() {
    let screenHeight =
      document.documentElement.clientHeight || document.body.clientHeight;
    let screenHeader = this.$refs.forHeight.offsetHeight;
    console.log(screenHeight, screenHeader);
    this.mainHeight = screenHeight - screenHeader;
  },
  methods: {
    login() {
      this.$router.push("/Main");
    }
  }
};
</script>
<style lang="scss" scoped>
.Login {
  width: 100%;
  height: 100%;
  .nav {
    padding-top: 2vmin;
    .el-row {
      .el-col {
        text-align: center;
        .el-link {
          display: inline-block;
          margin: 2vmin;
          font-size: 1.6vmin;
        }
      }
    }
  }
  .main {
    background-image: url("../assets/images/login/login-bkg.png");
    background-size: 100% 100%;
    overflow: hidden;
    .main-list {
      background-color: rgba($color: #000000, $alpha: 0.7);
      ul {
        width: 85%;
        margin: auto;
        margin-top: 17vmin;
        p {
          font-size: 2vmin;
          border-left: 5px solid #fff;
          padding-left: 0.5vmin;
          margin-bottom: 3vmin;
          color: #fff;
        }
        span {
          color: #fff;
        }
        .el-input {
          margin: 1.5vmin 0 3vmin 0;
        }
        button {
          width: 100%;
        }
      }
    }
  }
}
</style>
