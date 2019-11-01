<template>
    <div id="pay">
        <div id="login_title">
            <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
            <span id="login_title_center">我的优惠</span>
        </div>
        <div id="time">
            <p id="time_text">支付剩余时间</p>
            <p id="time_num"><span>00:</span><span v-text="minute+':'"></span><span v-text="second"></span></p>
        </div>
        <p id="pay_type_p">选择支付方式</p>
        <div id="pay_type">   
            <ul>
                <li>
                    <span class="iconfont type_i">&#xee0f;</span>
                    <span class="type_text">支付宝</span>
                    <el-radio v-model="radio" class="type_right" label="1">
                         <i class="el-icon-check"></i>
                    </el-radio>
                </li>
                <li>
                    <span class="iconfont type_i type_i2">&#xe620;</span>
                    <span class="type_text">微信</span>
                    <el-radio v-model="radio" class="type_right" label="2">
                        <i class="el-icon-check"></i>
                    </el-radio>
                </li>
            </ul>  
        </div>
        <div id="last">
            <button id="pay_btn" @click="pay_true()">确认支付</button>   
         </div>
    </div>
</template>

<script>
export default {
    name:'pay',
    data(){
        return{
            radio:"1",
            minutes:15,
            seconds:0
        }
    },
    mounted(){
        this.add();
    },
    methods:{
         router1(){
            this.$router.push({
                path:'/huiyuan',
                name:'huiyuan'
            })
        },
         num: function (n) {
        return n < 10 ? '0' + n : '' + n
      },
        add: function () {
        var _this = this
        var time = window.setInterval(function () {
          if (_this.seconds === 0 && _this.minutes !== 0) {
            _this.seconds = 59
            _this.minutes -= 1
          } else if (_this.minutes === 0 && _this.seconds === 0) {
            _this.seconds = 0
            window.clearInterval(time)
          } else {
            _this.seconds -= 1
          }
        }, 1000)
      },
      pay_true(){
          alert("当前环境无法支付,请打开官方APP进行付款");
      }
       
    },
     watch: {
      second: {
        handler (newVal) {
          this.num(newVal)
        }
      },
      minute: {
        handler (newVal) {
          this.num(newVal)
        }
      }
    },
    computed: {
      second: function () {
        return this.num(this.seconds)
      },
      minute: function () {
        return this.num(this.minutes)
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
    #time{
        text-align: center;
        padding: 1.64rem;
        background-color: #fff;
    }
    #time_text{
        color: #666;
        font-size: 1.4rem;
        margin-top:2.34rem;
        line-height: 1.92rem; 
    }
    #time_num{
        color: #333;
        line-height: 4.2rem;
        font-size: 3.5rem;
        margin-top: 0.7rem;
        margin-bottom: 2.3rem;
    }
    #pay_type_p{
        padding:1.64rem;
        font-size:1.6rem;
        line-height: 4.1rem;
        background-color: #f1f1f1;
        font-size: 1.6rem;
    }
    .type_i{
        font-size: 4.7rem;
        color: #3190e8;
        line-height: 6rem;
    }
    #pay_type>ul>li{
        padding: 0.93rem;
        background-color: #fff;
        margin-top: 1px;
    }
    .type_text{
        line-height: 5rem;
        color: #666;
        font-size: 1.6rem;
        margin-left: 0.6rem;
    }
    .type_right{
        float: right;
        line-height: 6rem;
        color: white;
    }
    .type_i2{
        color: #4cd964;
    }
    #last{
        text-align: center;
        margin-top: 2rem;
    }
    #pay_btn{
        color: white;
        background-color: #4cd964;
        width: 35rem;
        height: 4.2rem;
        font-size: 1.6rem;
        border: none;
        border-radius: 0.5rem;
    }
    #pay_type>ul>li .el-radio__label{
        color: rgb(150, 142, 142);
    }
</style>