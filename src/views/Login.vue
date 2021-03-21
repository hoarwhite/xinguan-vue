<template>
    <!-- 登陆表单的容齐 -->
    <div class = "login_container">
        <!-- 登陆区域 -->
        <div class = "login_box">
            <!-- 头像 -->
            <div class = "avator_box">
                <img src ="../assets/img/logo.82b9c7a5.png">
            </div>
            <!-- 表单 -->
    <el-form :model="loginForm" :rules="loginrules" ref="loginForm" label-width="0px" class="login_form">
    <el-form-item prop="username">
    <el-input v-model="loginForm.username" prefix-icon="el-icon-user-solid"></el-input>
    </el-form-item>
    <el-form-item prop="password">
    <el-input v-model="loginForm.password" prefix-icon="el-icon-lock"></el-input>
    </el-form-item>
    <el-form-item prop="verifyCode">
      <div class="verifyCode_box">
    <el-input v-model="loginForm.verifyCode" prefix-icon="el-icon-mobile" class="verifyCode"></el-input>
    <img src="../assets/img/msFXK1.gif" class="verify_img">
      </div>
    </el-form-item>
    <el-form-item class="login-btn">
        <el-button type="primary" @click="submitForm('loginForm')">立即创建</el-button>
        <el-button @click="resetForm('loginForm')">重置</el-button>
    </el-form-item>
    </el-form>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      loginForm: {
        username: '',
        passwprd: '',
        verifyCode: ''
      },
      loginrules: {
        username: [
          { required: true, message: '请输入用户名称', trigger: 'blur' },
          { min: 3, max: 16, message: '长度在 3 到 16 个字符', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入登陆密码', trigger: 'blur' },
          { min: 3, max: 16, message: '长度在 3 到 16 个字符', trigger: 'blur' }
        ],
        verifyCode: [
          { required: true, message: '请输入验证码', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    submitForm (formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          this.$router.push('/main')
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    resetForm (formName) {
      this.$refs[formName].resetFields()
    }
  }
}

</script>

<style lang="less" scoped>
    .login_container{
        height: 100%;
        background-color: aquamarine;
    }
    .login_box{
        width: 450px;
        height: 380px;
        background-color: #FFFFFF;
        border-radius: 3px;
        position: absolute; //居中
        left: 50%;
        top: 60%;
        transform: translate(-50%, -50%);
    }
    .avator_box{
        width: 130px;
        height: 130px;
        border: 1px solid #eeeeee;
        border-radius: 50%;
        padding: 10px;
        box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
        margin: -65px auto;
        background-color: #FFFFFF;

        img{
            width: 100%;
            height: 100%;
            border-radius: 100%;
            background-color: black;
        }
    }
    .login_form{
        position: absolute;
        bottom: 0px;
        width: 100%;
        padding: 0px;
        box-sizing: border-box;
    }
    .login_btn{
        display: flex;
        justify-content: flex-end;
    }
    .verifyCode_box{
      display: flex;
      .verifyCode{
        width: 70%;
        justify-self: left;
      }
    }

    .verfifyCode_img{
      width: 30%;
      height: 45px;
      justify-content: flex-end;
    }

</style>
