<template>
  <div class="login-container">
    <el-form
      class="login-form"
      :model="loginForm"
      :rules="rules"
    >
      <div>
        <img class="login-log" src="@/assets/dikede/logo.png" alt="">
      </div>
      <el-form-item prop="mobile">
        <span class="svg-container el-icon-user-solid" />
        <el-input v-model="loginForm.mobile" />
      </el-form-item>
      <el-form-item prop="password">
        <!-- <span class="svg-container el-icon-user-solid" /> -->
        <span class="svg-container">
          <svg-icon icon-class="password" />
        </span>
        <el-input v-model="loginForm.password" />
        <span class="svg-container">
          <svg-icon
            :icon-class="passwordType === 'password' ? 'eye' : 'eye-open'"
          />
        </span>
        <!-- <span class="svg-container el-icon-user-solid" /> -->
      </el-form-item>
      <el-form-item prop="verify">
        <span class="svg-container el-icon-mobile-phone" />
        <el-input v-model="loginForm.verify" />
      </el-form-item>
      <el-button class="loginBtn">登录</el-button>
    </el-form>
  </div>
  <!-- 环境变量的作用
  1. 正常公司中 有几个环境 4 开发 dev 测试 test 预发 uat 线上 pro
  2. 在项目里如何配置这几个环境  通过 .env 配置 base api
  开发环境的接口前缀 /api
  线上环境的接口前缀 /prod-api
   -->
</template>
<script>

export default {
  name: 'Login',
  data() {
    return {

      loginForm: {
        mobile: '',
        password: '',
        verify: ''
      },
      // rules: {
      //   mobile: [
      //     { required: true, message: '输入值不能为空', trigger: 'blur' }
      //   ],
      //   password: [
      //     { required: true, message: '输入值不能为空', trigger: 'blur' }
      //   ],
      //   verify: [
      //     { required: true, message: '输入值不能为空', trigger: 'blur' }
      //   ]
      // }
    }
  },
  methods: {
  }
}
</script>

<style lang="scss">
/* 修复input 背景不协调 和光标变色 */
/* Detail see https://github.com/PanJiaChen/vue-element-admin/pull/927 */

$bg: #3b6baa;
$light_gray: #68b0fe;
$cursor: #fff;

@supports (-webkit-mask: none) and (not (cater-color: $cursor)) {
  .login-container .el-input input {
    color: $cursor;
  }
}

/* reset element-ui css */
.login-container {
      position: relative;
    height: 100%;
    width: 100%;
    overflow: hidden;
    background-repeat: no-repeat;
    background-size: cover;
    background-image: url('~@/assets/dikede/background.png');
  .el-input {
    display: inline-block;
    height: 47px;
    width: 85%;

    input {
      background: transparent;
      border: 0px;
      -webkit-appearance: none;
      border-radius: 0px;
      padding: 12px 5px 12px 15px;
      color: $light_gray;
      height: 47px;
      caret-color: $cursor;

      &:-webkit-autofill {
        box-shadow: 0 0 0px 1000px $bg inset !important;
        -webkit-text-fill-color: $cursor !important;
      }
    }
  }

  .el-form-item {
    border: 1px solid rgba(255, 255, 255, 0.1);
    // background: rgba(0, 0, 0, 0.1);
    border-radius: 5px;
    color: #454545;
    background: rgba(255, 255, 255, 0.7); // 输入登录表单的背景色
  }
  .el-form-item__error {
    color: #fff;
  }
  .loginBtn {
    background: #6478ed;
    height: 64px;
    line-height: 32px;
    font-size: 24px;
    width: 100%;
    margin-bottom: 30px;
    border: none;
    color: #fff;
  }
}
</style>

<style lang="scss" scoped>
$bg: #2d3a4b;
$dark_gray: #889aa4;
$light_gray: #68b0fe;

.login-container {
  min-height: 100%;
  width: 100%;
  background-color: $bg;
  overflow: hidden;

  .login-form {
   position: absolute;
    width: 518px;
    height: 388px;
    top: 50%;
    left: 50%;
    margin-top: -194px;
    margin-left: -259px;
    padding: 76px 35px 0;
    background: #fff;
    -webkit-box-shadow: 0 3px 70px 0 rgb(30 111 72 / 35%);
    box-shadow: 0 3px 70px 0 rgb(30 111 72 / 35%);
    border-radius: 10px;
  }
  .login-log{
     position: absolute;
    width: 96px;
    height: 96px;
    top: -46px;
    left: 50%;
    margin-left: -48px;
    }
  .svg-container {
    padding: 6px 5px 6px 15px;
    color: $dark_gray;
    vertical-align: middle;
    width: 30px;
    display: inline-block;
  }

.el-form-item__content {
    line-height: 50px;
    position: relative;
    font-size: 14px;
    display: flex;
    border: 1px solid;
    color: #e2e2e2;
    border-radius: 6px;
}
.el-icon-delete:before {
    content: "\e6d7";
    margin: auto;
    color: #889aa4;
}
  .title-container {
    position: relative;

    .title {
      font-size: 26px;
      color: $light_gray;
      margin: 0px auto 40px auto;
      text-align: center;
      font-weight: bold;
    }
  }

  .show-pwd {
    position: absolute;
    right: 10px;
    top: 7px;
    font-size: 16px;
    color: $dark_gray;
    cursor: pointer;
    user-select: none;
  }
}
</style>
