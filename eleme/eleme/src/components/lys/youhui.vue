<template>
  <div id="redbag">
        <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
              <span id="login_title_center">我的优惠</span>
        </div>
        <div id="both">
        <p id="top_one">
        <router-link to="/hongbao" tag="span" exact><span id="top_one_left">红包</span></router-link>
        <router-link to="/jinjuan" tag="span"><span id="top_one_right">商家代金券</span></router-link>
        </p>
        <router-view></router-view>
        
        </div>
  </div>
</template>

<script>
export default {
    name:"youhui",
    data(){
        return{
            data:{},//传过来的信息
 
        }
    },
    created(){
        this.data=this.$route.query.data;
        console.log(this.data);

    },
    methods:{
       router1(){
            this.$router.push({
                path:'/minindex',
                name:'minindex',
                query:{
                    data:this.data
                }
            })
        },
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
    #top_one{
        padding: 1em 6rem;
        line-height: 2rem;
        color: #333;
        font-size: 1.52rem;
        background-color: #fff;
        font-weight: 400;
        
    }
    #top_one_left{
        padding-bottom: 0.5rem;

    }
    #top_one_right{
        float: right;
        padding-bottom: 0.5rem;
    }
    .router-link{
        color: #333;
    }
    .router-link-active{
        color: #3190e8;
        border-bottom: 2px solid #3190e8;
    }
    
</style>