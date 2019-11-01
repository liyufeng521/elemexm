<template>
  <div id="user_XG">
        <div id="login_title">
              <span class="el-icon-arrow-left" @click="routergo()" id="login_title_i"></span>
              <span id="login_title_center">修改用户名</span>
        </div>
        <div id="user_form">
            <input type="text" placeholder="修改用户名">
            <p>用户名只能修改一次(5~24字符之间)</p>
            <div><button>确认修改</button></div>
        </div>
  </div>
</template>

<script>
export default {
    name:"user_xiugai",
    data(){
        return{

        }
    },
    methods:{
        routergo(){
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
   
    #user_form>input{
        width: 37.5rem;
        padding: 0.47rem 1rem;
        background-color: #fff;
        color: #999;
        margin-top: 1rem;
        line-height: 4rem;
    }
    #user_form>p{
        color: #666;
        font-size: 1rem;
        padding: 1rem 0 2.3rem 1rem;
    }
    #user_form button{
        width: 35rem;
        height: 4.6rem;
        color: #fff;
        font-size: 1.64rem;
        border: none;
        background-color: #3190e8;
        border-radius: 0.5rem;
    }
    #user_form>div{
        text-align: center;
    }
</style>