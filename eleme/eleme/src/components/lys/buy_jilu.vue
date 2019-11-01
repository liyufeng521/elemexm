<template>
  <div id="buy">
        <div id="login_title">
            <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
            <span id="login_title_center">购买记录</span>
        </div>
        <div id="buy_i">
            <span class="iconfont">&#xe60b;</span>
            <p>没有购买记录</p>
        </div>
  </div>
</template>

<script>
export default {
    name:'buy_jilu',
    data(){
        return{

        }
    },
    methods:{
        router1(){
            this.$router.push({
                name:'huiyuan',
                path:'/huiyuan'
            })
        }
    }
}
</script>

<style scoped>
@font-face {
  font-family: 'iconfont';  /* project id 1477980 */
  src: url('http://at.alicdn.com/t/font_1477980_63ps931m0of.eot');
  src: url('http://at.alicdn.com/t/font_1477980_63ps931m0of.eot?#iefix') format('embedded-opentype'),
  url('http://at.alicdn.com/t/font_1477980_63ps931m0of.woff2') format('woff2'),
  url('http://at.alicdn.com/t/font_1477980_63ps931m0of.woff') format('woff'),
  url('http://at.alicdn.com/t/font_1477980_63ps931m0of.ttf') format('truetype'),
  url('http://at.alicdn.com/t/font_1477980_63ps931m0of.svg#iconfont') format('svg');
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
    #buy_i{
        margin-top: 11.7rem;
        text-align: center;
    }
    #buy_i>span{
        font-size: 9rem;
        color: #3190e8;
    }
    #buy_i>p{
        margin-top: 1.875rem;
        color: #999;
        font-size: 1.4rem;
        line-height: 1.9rem;
    }
</style>