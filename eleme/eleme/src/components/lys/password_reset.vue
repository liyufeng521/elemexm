<template>
  <div id="app">
      <div id="login">
          <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
              <span id="login_title_center">重置密码</span>
          </div>
          <input placeholder="账号" v-model="username" type="text" id="input_user">
          <div id="pass_both">
          <input placeholder="旧密码" v-model="oldpassWord" type="text">
          <input placeholder="请输入新密码" v-model="newpassword" type="text">
          <input placeholder="请确认新密码" v-model="confirmpassword" type="text">
          </div>
          <div id="code_text">
          <input placeholder="验证码" v-model="captcha_code" type="text">  
              <img id="code_img" :src="code" alt="">
              <span id="code_text1">看不清</span>
              <span id="code_text2" @click="gaicode()">换一张</span>
          </div>
           <el-button type="success" id="login_btn" @click="gaiPass()">确认修改</el-button>

      </div>
  </div>
</template>

<script>
export default {
    name:"password_reset",
    data(){
        return{
            value:false,
            username:"",
            oldpassWord:"",
            newpassword:"",
            cofirmpassword:"",
            captcha_code:"",
            code:""
        }
    },
    created(){
        this.getCode();
    },
    methods:{
        //获取验证码
        getCode(){
              const api = "https://elm.cangdu.org/v1/captchas";
              this.$http({
                  url:api,
                  method:"post",
                  withCredentials:true,
                  data:{

                  },
              }).then(res=>{
                //   console.log(res);
                  this.code=res.data.code;
              })
        },
        gaicode(){
            this.getCode();
        },
        
        gaiPass(){
            const api = "https://elm.cangdu.org/v2/changepassword";
            this.$http({
                url:api,
                method:"post",
                withCredentials:true,
                data:{
                    username:this.username,
                    oldpassWord:this.oldpassWord,
                    newpassword:this.newpassword,
                    confirmpassword:this.confirmpassword,
                    captcha_code:this.captcha_code
                }
            }).then(res=>{
                // console.log(res);
                if(res.data.message){
                    alert(res.data.message);
                    return;
                }
               
            })
        },
        router1(){
            this.$router.go(-1);
        }

    }
}
</script>

<style scoped>
    #login_title{
        height: 4.57rem;
        background-color: #3190e8;
        text-align: center;
    }
    #login_title_i{
        font-size: 2rem;
        margin-left: 1rem;
        color: white;
        line-height: 4.57rem;
        float: left;
    }
    #login_title_center{
        font-size: 1.875rem;
        color: white;
        font-weight: bold;
        line-height: 4.57rem;
        margin-right: 2rem;
    }
    #input_user {
        margin-top: 1.5rem;
    }
    input{
        width: 100%;
        height: 4.9rem;
        font-size: 1.75rem;
        color: #666;
        padding-left: 1.5rem;
        margin-top: 1px;
    }
    #pass_both{
        position: relative;
    }
    .pass_btn{
        position: absolute;
        top: 1.5rem;
        right: 2rem;
    }
    #code_text{
        position: relative;
    }
    #code_text1{
        position: absolute;
        top: 0.8rem;
        right:2rem;
        color: #666;
        font-size: 1.29rem;
    }
    #code_text2{
        position: absolute;
        top: 3rem;
        right: 2rem;
        color: #3b95e9;
        font-size: 1.29rem;
    }
    #code_img{
        position: absolute;
        top: 1.2rem;
        right: 7rem;
    }
    .code_p{
        color: #ff0000;
        line-height: 3rem;
        font-size: 1.2rem;
        padding-left: 1.5rem;
    }
    #login_btn{
        background-color: #4cd964;
        color: white;
        font-size: 1.6rem;
        margin: 0 auto;
        width: 35rem;
        display: block;
        margin-top: 2.5rem;
    }
    #pass_gai{
        color: #3b95e9;
        font-size: 1.4rem;
        margin-top: 3rem;
        float: right;   
    }
</style>