<template>
  <div id="app">
      <div id="login_title">
            <span class="el-icon-arrow-left" id="login_title_i" @click="routergo()"></span>
            <span id="login_title_center">兑换红包</span>
        </div>
        <div id="dw">
        <div id="code_text">
            <input type="text" placeholder="请输入兑换码" id="duihuan" v-model="exchange_code">
            <input placeholder="验证码" v-model="captcha_code" type="text">  
              <div id="code_right">
                 <img id="code_img" :src="code" alt="">
                 <span id="code_text1">看不清</span>
                 <span id="code_text2" @click="gaipass()">换一张</span>
              </div>
              <input type="button" value="兑换" @click="huan()" disabled id="btn">
          </div>
        </div>
  </div>
</template>

<script>
export default {
    name:'hongbao_duihuan',
    data(){
        return{
            code:'',
            captcha_code:'',
            exchange_code:''
        }
    },
    created(){
        this.getCode();
    },
        methods:{
         getCode(){
              const api = "https://elm.cangdu.org/v1/captchas";
              this.$http({
                  url:api,
                  method:"post",
                  withCredentials:true,
                  data:{

                  },
              }).then(res=>{
                  console.log(res);
                  this.code=res.data.code;
              })
        },
        gaipass(){
            this.getCode();
        },
        huan(){
            alert(无效的兑换码);
        },
         routergo(){
            this.$router.go(-1);
        }
    },
     watch:{
            exchange_code(newV,oldV){
                if(newV !=""){
                    if(this.captcha_code.length==4){
                         this.isDisabled=false
                    }
                }else {
                    this.isDisabled=true
                }
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
     input{
        width: 100%;
        height: 4.9rem;
        font-size: 1.75rem;
        color: #666;
        padding-left: 1.5rem;
        margin-top: 1px;
        border-radius: 0.7rem;;
        margin-top: 2rem;
        box-sizing: border-box;
    }
     #code_text{
        position: relative;
        padding: 2rem;
    }
    #code_text1{
        position: absolute;
        top: 10rem;
        right:4rem;
        color: #666;
        font-size: 1.29rem;
    }
    #code_text2{
        position: absolute;
        top: 12rem;
        right: 4rem;
        color: #3b95e9;
        font-size: 1.29rem;
    }
    #code_img{
        position: absolute;
        top: 10rem;
        right: 9rem;
    }
    .code_p{
        color: #ff0000;
        line-height: 3rem;
        font-size: 1.2rem;
        padding-left: 1.5rem;
    }
    #duihuan{
       margin-top: 0;
    }
    #btn{
        /* background-color: #3b95e9; */
        color: white;
    } 
</style>