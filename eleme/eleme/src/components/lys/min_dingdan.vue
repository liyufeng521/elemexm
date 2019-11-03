<template>
  <div id="DD">
        <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
              <span id="login_title_center">订单列表</span>
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
    name:'min_dingdan',
    data(){
        return {

        }
    },
    methods:{
        router1(){
            this.$router.push({
                path:'/minindex',
                name:'minindex'
            })
           
        },
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