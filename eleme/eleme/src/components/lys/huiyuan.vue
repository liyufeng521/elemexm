<template>
    <div id="HY">
        <div id="login_title">
            <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
            <span id="login_title_center">会员中心</span>
        </div>
        <p id="hy_one"><span>为账户</span><span id="user" v-text="user"></span><span>购买会员</span></p>
        <ul id="lists">
            <li id="tequan" @click="router2()">
                <span id="tequan_left">会员特权</span>
                <span  class="tequan_right">></span>
                <span class="tequan_right">会员说明</span>   
            </li>
            <li>
                <i class="iconfont iii">&#xe61e;</i>
               <div>
                <h4>减免配送费</h4>
                <p>每月减免30单，每日可减免3单，每单最高减4元</p>
                <p>蜂鸟专送专享</p>
               </div>
            </li>
            <li>
                <i class="iconfont iii">&#xe7bf;</i>
                <div>
                    <h4 data-v-4e602cfc="">减免配送费</h4>
                <p>每月减免30单，每日可减免3单，每单最高减4元</p>
                <p>蜂鸟专送专享</p>
                </div>
            </li>
        </ul>
        <p class="kt">开通会员</p>
        <p class="kt"><span>一个月</span><span id="kt_one">￥20</span><button id="kt_two"  @click="router3()">购买</button></p>
        <p class="last" @click="router4()"><span>兑换会员</span><span class="last_two">></span><span class="last_one">使用卡号卡密</span></p>
        <p class="last" @click="router5()"><span>购买记录</span><span class="last_two">></span><span class="last_one">开发票</span></p>
    </div>
</template>

<script>
export default {
    name:'huiyuan',
    data(){
        return{
            user:"",
        }
    },
    methods:{
        router1(){
            this.$router.push({
                path:'/minindex',
                name:'minindex'
            })
        },
        router2(){
            this.$router.push({
                name:'huiyuan_shuoming',
                path:'/huiyuan_shuoming' 
            })
        },
        router3(){
            this.$router.push({
                name:'pay',
                path:'/pay'
            })
        },
        router4(){
            this.$router.push({
                name:'duihuan_huiyuan',
                path:'/duihuan_huiyuan'
            })
        },
        router5(){
            this.$router.push({
                name:'buy_jilu',
                path:'/buy_jilu'
            })
        }
    }

}
</script>

<style scoped>
@font-face {
  font-family: 'iconfont';  /* project id 1477980 */
  src: url('http://at.alicdn.com/t/font_1477980_p0u7ge3bd1r.eot');
  src: url('http://at.alicdn.com/t/font_1477980_p0u7ge3bd1r.eot?#iefix') format('embedded-opentype'),
  url('http://at.alicdn.com/t/font_1477980_p0u7ge3bd1r.woff2') format('woff2'),
  url('http://at.alicdn.com/t/font_1477980_p0u7ge3bd1r.woff') format('woff'),
  url('http://at.alicdn.com/t/font_1477980_p0u7ge3bd1r.ttf') format('truetype'),
  url('http://at.alicdn.com/t/font_1477980_p0u7ge3bd1r.svg#iconfont') format('svg');
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
    #hy_one{
        padding-left: 1.6rem;
        line-height: 4.6rem;
        color: #666;
        font-size: 1.4rem;
    }
    #hy_one>#user{
        color: #333;
    }
    #lists>li{
        background-color: #fff;
        margin-top: 1px;
        padding: 2rem 1.6rem;
        height: 6rem;
    }
   #lists #tequan{
        padding: 0 1.6rem;
        height: 4.64rem;
    }
    #tequan_left{
        line-height: 4.7rem;
        color: #333;
        font-size: 1.64rem;
    }
    .tequan_right{
        line-height: 4.7rem;
        color: #999;
        font-size: 1.4rem;
        margin-left: 0.5rem;
        float: right;
    }
    .iii{
        float: left;
        font-size: 40px;
        color: #3190e8;
    }
    li>div>h4{
        color:#333;
        font-size: 1.64rem;
        line-height: 2.16rem;
    }
    li>div>p{
        color: #999;
        font-size: 1.17rem;
        line-height: 1.52rem;
    }
    li>div{
        float: left;
        margin-left: 1.5rem;
    }
    .kt{
        background-color: #fff;
        margin-top: 1.2rem;
        padding: 0 1.6rem;
        line-height: 4.64rem;
        font-size: 1.6rem;
        margin-top: 1px;
    }
    #kt_one{
        margin-left: 1rem;
        color: #ff6600;
    }
    #kt_two{
        float: right;
        color: #ff6600;
        border: 1px solid #ff6600;
        border-radius: 0.5rem;;
        background-color: #fff;
        padding: 0.5rem 1.5rem;
        margin-top: 0.8rem;
    }
    .last{
        margin-top: 1.2rem;
        line-height: 4.7rem;
        padding: 0 1.6rem;
        color: #333;
        font-size: 1.64rem;
        background-color: #fff;
    }
    .last_one,.last_two{
        float: right;
        color: #999;
        font-size: 1.4rem;
    }
    .last_two{
        margin-left: 0.5rem;
        font-size: 1.6rem;
    }
</style>