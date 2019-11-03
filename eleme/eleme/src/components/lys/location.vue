<template>
  <div id="location">
        <div id="login_title">
            <span class="el-icon-arrow-left" id="login_title_i" @click="routergo()"></span>
            <span id="login_title_center">下载</span>
        </div>
        <div id="conent">
            <i class="iconfont conent_i">&#xe68c;</i>
            <p id="conent_text">下载饿了么APP</p>
            <input type="button" value="下载" id="conent_btn" @click="kshow()">
        </div>
        <!-- 弹出框 -->
           <div id="mask">
               <div id="kuang">
               <span class="el-icon-warning-outline kuang_i"></span> 
               <p>IOS用户请前往APPStore下载</p>
               <button @click="knone">确认</button>
               </div>
           </div>
  </div>
</template>

<script>
export default {
    name:'location',
    data(){
        return{

        }
    },
     methods:{
        routergo(){
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
    margin-top: 18rem;
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

@font-face {
  font-family: 'iconfont';  /* project id 1477980 */
  src: url('http://at.alicdn.com/t/font_1477980_2buov3gi6du.eot');
  src: url('http://at.alicdn.com/t/font_1477980_2buov3gi6du.eot?#iefix') format('embedded-opentype'),
  url('http://at.alicdn.com/t/font_1477980_2buov3gi6du.woff2') format('woff2'),
  url('http://at.alicdn.com/t/font_1477980_2buov3gi6du.woff') format('woff'),
  url('http://at.alicdn.com/t/font_1477980_2buov3gi6du.ttf') format('truetype'),
  url('http://at.alicdn.com/t/font_1477980_2buov3gi6du.svg#iconfont') format('svg');
}
.iconfont{
    font-family:"iconfont" !important;
    font-size:16px;font-style:normal;
    -webkit-font-smoothing: antialiased;
    -webkit-text-stroke-width: 0.2px;
    -moz-osx-font-smoothing: grayscale;
    }
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
    #conent{
        text-align: center;
    }
    .conent_i{
        font-size: 18rem;
        margin: 0 auto;
        margin-top: 2.3rem;
        display: inline-block;
        color: #3190e8;
    }
    #conent_text{
        color: #666;
        font-size: 1.875rem;
        line-height: 2.5rem;
        margin-bottom: 2.34rem;
        margin-top: 1rem;
    }
    #conent_btn{
        border: none;
        width: 35rem;
        height: 4.1rem;
        background-color: #4cd964;
        font-size: 1.6rem;
        color: white;
        border-radius: 0.6rem;
    }
</style>