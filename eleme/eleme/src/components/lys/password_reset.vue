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
          <input placeholder="请确认新密码" v-model="cofirmpassword" type="text">
          </div>
          <div id="code_text">
          <input placeholder="验证码" v-model="captcha_code" type="text">  
              <img id="code_img" :src="code" alt="">
              <span id="code_text1">看不清</span>
              <span id="code_text2" @click="gaicode()">换一张</span>
          </div>
           <el-button type="success" id="login_btn" @click="gaiPass()">确认修改</el-button>

      </div>
       <!-- 弹出框 -->
           <div id="mask">
               <div id="kuang">
               <span class="el-icon-warning-outline kuang_i"></span> 
               <p v-text="message"></p>
               <button @click="knone()">确认</button>
               </div>
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
            code:"",
            message:""
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
                    confirmpassword:this.cofirmpassword,
                    captcha_code:this.captcha_code
                }
            }).then(res=>{
                // console.log(res);
                if(res.data.message){
                    this.message=res.data.message;
                    this.gaicode();
                    this.kshow();
                    this.captcha_code="";
                    return;
                }
               
            })
        },
        router1(){
            this.$router.go(-1);
        },
        kshow(){
            $("#mask").css("display","block");
        },
        knone(){
            $("#mask").css("display","none");
        }

    }
}
</script>

<style scoped>
/* 弹出框 */
#mask{
    width: 37.5rem;
    height: 66.7rem;
    position: fixed;
    top: 0;
    left: 0;
    background-color:rgba(0,0,0,0);
    display: none;
}
#kuang{
    width: 28rem;
    margin: 0 auto;
    margin-top: 12rem;
    text-align: center;
    background-color: #fff;
    border-radius: 1rem;
    overflow: hidden;
}
.kuang_i{
    font-size: 7rem;
    margin-top: 2rem;
    color: #fe6d47;
}
#kuang>p{
    color: #333;
    font-size: 1.6rem;
    margin-top: 2rem;
}
#kuang>button{
    width: 28rem;
    height: 4rem;
    background-color: #4cd964;
    color: #fff;
    font-size: 1.875rem;
    margin-top: 2rem;
    border: none;
}

    #login_title{
        height: 4.57rem;
        background-color: #3190e8;
        text-align: center;
        position: fixed;
        top: 0;
        left: 0;
        width: 37.5rem;
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
        margin-top: 6.5rem;
    }
    input{
        width: 37.5rem;
        height: 4.9rem;
        font-size: 1.75rem;
        color: #666;
        padding-left: 1.5rem;
        margin-top: 1px;
        box-sizing: border-box;
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