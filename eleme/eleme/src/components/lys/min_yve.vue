<template>
    <div id="yve">
         <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
              <span id="login_title_center">我的余额</span>
          </div>
          <div id="yve_qian">
              <div id="yve_qian_small">
              <span id="yue_qian_text_left">当前余额</span>
                <span class="iconfont" id="yue_qian_text_right_i">&#xe64d;</span>
                <span id="yue_qian_text_right" @click="router2()">余额说明</span>
                <p id="money_fath"><span id="money">0.00</span><span id="money_text">元</span></p>
                <!-- <input type="button" value="提现">  -->
                 <div id="money_btn_fath"><el-button type="info" id="money_btn" disabled>提现</el-button></div>
                </div>      
          </div>
          <span id="yue_text">交易明细</span>
          <div id="money_last">
              <i class="iconfont">&#xe60b;</i>
              <p>暂无明细记录</p>
           </div>

    </div>
</template>

<script>
export default {
    name:"yve",
    data(){
        return{

        }
    },
    methods:{
        router1(){
            this.$router.push({
                name:'minindex',
                path:'/minindex'
            })
        },
        router2(){
            this.$router.push({
                name:'yve_shuoming',
                path:'/yve_shuoming'
            })
        }
    }
}
</script>

<style scoped>
@font-face {
  font-family: 'iconfont';  /* project id 1477980 */
  src: url('http://at.alicdn.com/t/font_1477980_9f01tem0cbp.eot');
  src: url('http://at.alicdn.com/t/font_1477980_9f01tem0cbp.eot?#iefix') format('embedded-opentype'),
  url('http://at.alicdn.com/t/font_1477980_9f01tem0cbp.woff2') format('woff2'),
  url('http://at.alicdn.com/t/font_1477980_9f01tem0cbp.woff') format('woff'),
  url('http://at.alicdn.com/t/font_1477980_9f01tem0cbp.ttf') format('truetype'),
  url('http://at.alicdn.com/t/font_1477980_9f01tem0cbp.svg#iconfont') format('svg');
}
.iconfont{
    font-family:"iconfont" !important;
    font-size:16px;font-style:normal;
    -webkit-font-smoothing: antialiased;
    -webkit-text-stroke-width: 0.2px;
    -moz-osx-font-smoothing: grayscale;}
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
    #yve_qian{
        background-color: #3190e8;
        margin-top: 1px;
        padding: 1rem;
    }
    #yve_qian>div{
        background-color: #fff;
        border-radius: 0.5rem;
        padding: 1rem;
    }
    #yue_qian_text_left{
         font-size: 1.29rem;
         color: #666;
    }
    #yve_qian_small{
        position: relative;
    }
    #yue_qian_text_right_i{
        position: absolute;
        top: 0.5rem;
        right: 6.5rem;
        color: #3190e8;
        font-size: 1.8rem;
    }
     #yue_qian_text_right{
         color: #3190e8;
         font-size: 1.29rem;
         float: right;
     }
     #money_fath{
          margin-top: 1rem;
     }
     #money{
         color: #333;
         font-size: 4.2rem;
     }
     #money_text{
         color: #333;
         font-size: 1.64rem;
         margin-left: 1rem;
     }
     #money_btn_fath{
         text-align: center;
     }
     #money_btn{  
         width: 90%;
         margin: 0 auto;
         margin-top:2.4rem;
     }
     #yue_text {
         font-size: 1.4rem;
         color: #999;
         padding-left: 1.2rem;
         line-height: 4.6rem;
     }
     #money_last{
         text-align: center;
         margin-top: 3rem;
     }
     #money_last>i{
         font-size: 10rem;
         color: #999;
     }
     #money_last>p{
        margin-top: 1.5rem;
        color: #666;
        font-size: 1.64rem;
     }
</style>