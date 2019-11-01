<template>
  <div id="app">
      <div id="min">
         <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i"></span>
              <span id="login_title_center">我的</span>
          </div>
          <div id="min_min" @click="router1()">
               <div class="block"><el-avatar :size="59" :src="circleUrl"></el-avatar></div>
               <span id="min_login" v-text="username"></span>
               <span class="el-icon-mobile-phone"></span>
               <span id="min_nophone" v-text="mobile"></span>
               <span class="el-icon-arrow-right top_i"></span>
          </div>
         <ul id="min_juan">
           <li @click="router2()">
            <span class="juan_first" id="first_one">0.00</span>
            <span class="juan_second">元</span>
            <p class="juan_title">我的余额</p>
           </li>
           <li @click="router8()">
              <span class="juan_first" id="first_two" v-text="gift_amount"></span>
              <span class="juan_second">个</span>
              <p class="juan_title">我的优惠</p>
           </li>
           <li @click="router3()">
             <span class="juan_first" id="first_three">0</span>
             <span class="juan_second">分</span>
             <p class="juan_title">我的积分</p>
           </li>
         </ul>
         <div class="cle"></div>
          <ul id="min_lists">
           <li @click="router4()">
              <i class="iconfont">&#xe600;</i>
              <span class="">我的订单</span>
              <span class="el-icon-arrow-right right_i"></span>
           </li>
           <li>
              <i class="iconfont" style="color:orange">&#xe60e;</i>
              <span>积分商城</span>
              <span class="el-icon-arrow-right right_i"></span>
           </li>
           <li @click="router7()">
              <i class="iconfont" style="color:gold" >&#xe607;</i>
              <span>饿了么会员卡</span>
              <span class="el-icon-arrow-right right_i"></span>
           </li>
           <li @click="router6()">
              <i class="iconfont"  style="color:blue">&#xe61d;</i>
              <span>服务中心</span>
              <span class="el-icon-arrow-right right_i"></span>
           </li>
           <li @click="router5()">
              <i class="iconfont" style="color:#3190e8">&#xe68c;</i>
              <span>下载饿了么APP</span>
              <span class="el-icon-arrow-right right_i"></span>
           </li>
         </ul>
      </div>
      <div id="dibu">
          <ul id="ul2">
              <li @click="shouye()">
                  <i class="el-icon-eleme"></i>
                  <p>外卖</p>
              </li>
              <li @click="shopsousuo()"> 
                  <i class="el-icon-discover"></i>
                  <p>搜索</p>
              </li>
              <li @click="dingdan()">
                  <i class="el-icon-tickets"></i>
                  <p>订单</p>
              </li>
              <li id="waimai">
                 <i class="el-icon-user"></i>
                 <p>我的</p>
              </li>
          </ul>
      </div>
  </div>
</template>

<script>
export default {
  name:"minindex",
  data(){
    return{
      circleUrl: "https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png",
      username:"",
      mobile:"",
      gift_amount:"0",
      data:{}
    }
  },
  created(){
    this.getuser();
 
  },
  methods:{
    router1(){
      if(this.username=="登录/注册"){
        this.$router.push({
        path:'/login',
        name:'login',
      })
      }else{
        this.$router.push({
        path:'/zhanghu',
        name:'zhanghu',
        query:{
         data:this.data,

        }
      })
      }
    },
    router2(){
      this.$router.push({
        path:'/yve',
        name:'yve',
      })
    },
     router3(){
      this.$router.push({
        path:'/min_jifen',
        name:'min_jifen',
      })
    },
    router4(){
      this.$router.push({
        path:'/min_dingdan',
        name:'min_dingdan',
      })
    },
    router5(){
      this.$router.push({
        path:'/location',
        name:'location',
      })
    },
    router6(){
      this.$router.push({
        path:'/fuwu',
        name:'fuwu'
      })
    },
    router7(){
      this.$router.push({
        path:'/huiyuan',
        name:'huiyuan'
      })
    },
    router8(){
      this.$router.push({
        path:'/youhui',
        name:'youhui',
        query:{
         data:this.data
        }
      })
    },
    // 编程式跳转--到李雨页面
    shopsousuo(){
        this.$router.push({
        path:"/lyf_shopsousuo",
        query:{
            data:this.dizhi
        }
      }); 
        },
        dingdan(){
        this.$router.push({
        path:"/lyf_dingdan",
        query:{
            
        }
      }); 
        },
        shouye(){
        this.$router.push({
        path:"/lyf_shouye",
        query:{
        }
      }); 
        },

    getuser(){
      const api = "https://elm.cangdu.org/v1/user";
      this.$http({
        url:api,
        method:"get",
        withCredentials:true,
      }).then(res=>{
        // console.log(res.data);
        this.data=res.data;
        console.log(this.data);
        if(!res.data.username){
          this.username= "登录/注册"
        }else{
          this.username=res.data.username;
          this.gift_amount=res.data.gift_amount;
          // console.log(this.gift_amount);
        };
        if(!res.data.mobile){
          this.mobile="暂无绑定手机号"
        }else{
          this.mobile=res.data.mobile;
        }
        
      })
    }
  }
  
}
</script>

<style scoped>
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
    #min_min{
      margin-top: 1px;
      background-color: #3190e8;
      position: relative;
    }
    .block{
      width: 5.9rem;;
      height: 5.9rem;
      padding: 1.5rem;
    }
    #min_login{
      color: white;
      font-size: 1.875rem;
      font-weight: 500;
      position: absolute;
      top: 2rem;
      left: 9rem;
    }
    .el-icon-mobile-phone{
      position: absolute;
      color: white;
      left: 9rem;
      top: 5rem;
    }
    #min_nophone{
      color: white;
      font-size: 1.35rem;
      position: absolute;
      left: 10.8rem;
      top: 5rem;
    }
    .top_i{
     position: absolute;
     top:3.7rem;
     right: 1.5rem;
     color: white;
     font-size: 2rem; 
    }
    #min_juan>li{
      width: 33%;
      margin-right: 1px;
      box-sizing: border-box;
      float: left;
      background-color: white;
      text-align: center;
    }
  .juan_first{
    display:inline-block;
      margin-top: 2rem;
      padding-bottom: 1.1rem;
      font-weight: 600;
  }
  .juan_second{
    color: #333;
    font-size: 1.3rem;
  }
  .juan_title{
    margin-bottom:1.1rem;
    color: #666;
    font-size: 1.34rem;
  }
  #first_one{
    font-size: 2.8rem;
    color: #ff9900;
  }
  #first_two{
    font-size: 2.8rem;
    color: #ff5f3e;
  }
  #first_three{
    font-size: 2.8rem;
    color: #6ac20b;
  }
  #min_lists{
    margin-top: 1rem;
  }
  #min_lists>li{
    margin-top: 1px;
    padding-left: 2rem;
    padding: 1.5rem;
    background-color: #fff;
    color: #333;
    font-size: 1.6rem;
  }
  .cle{
    clear: both;
    height: 0px;
  }
  .right_i{
    float: right;
  }
  li>i{
    padding-right: 0.5rem;
  }
  /* 底部 */
  #dibu,#dibutianchong{
    width: 37.5rem;
    height: 4.5rem;
}
#dibu{
    position: fixed;
    bottom: 0rem;
}
#dibu i {
    font-size: 2rem;
}
#dibu>ul>li{
    display: inline-block;
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    border: none;
    width: 24%;
    height: 4.5rem;
    text-align: center;
    fill: #ccc;
    padding-top: 0.4rem;
}
#dibu>ul p{
    font-size: 1.3rem;
    color: #666666;
    height: 2rem;
    line-height: 2rem;
}
#app #dibu>#ul2>#waimai>p,#app #dibu>#ul2>#waimai{
    color: #3190e8;
}
</style>