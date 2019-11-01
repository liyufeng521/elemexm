<template>
<div id="app">
        <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i" @click="routergo()"></span>
              <span id="login_title_center">历史红包</span>
        </div>
        <ul id="lists">
            <li class="list" :key="i" v-for="(v,i) in hbh">
                <p class="xuxian"></p>
                <div class="list_left">
                    <p class="list_money"><span>￥</span><span class="list_money_num">{{v.amount}}</span><span>.0</span></p>
                    <p class="man_money">满{{v.sum_condition}}元可用</p>
                </div>
                <div class="list_center">
                    <p class="fenxiang">{{v.name}}</p>
                    <p class="data">{{v.end_date}}到期</p>
                    <p class="phone">限收货手机号为：{{v.phone}}</p>
                </div>
                <span class="list_right iconfont">&#xe650;</span>
            </li>
        </ul>
</div>
</template>

<script>
export default {
    name:'hongbao_history',
    data(){
        return{
            hbh:[],
        }
    },
    created(){
        this.getHBH();
    },
    methods:{
        getHBH(){
            const api = "https://elm.cangdu.org/promotion/v2/users/1/expired_hongbaos?limit=20&offset=0";
            this.$http({
                url:api,
                method:'get',
            }).then(res=>{
                console.log(res.data);
                this.hbh=res.data;
            })
        },
        routergo(){
            this.$router.go(-1);
        }
    }
}
</script>

<style scoped>
@font-face {
  font-family: 'iconfont';  /* project id 1477980 */
  src: url('http://at.alicdn.com/t/font_1477980_cibtf6bi5zj.eot');
  src: url('http://at.alicdn.com/t/font_1477980_cibtf6bi5zj.eot?#iefix') format('embedded-opentype'),
  url('http://at.alicdn.com/t/font_1477980_cibtf6bi5zj.woff2') format('woff2'),
  url('http://at.alicdn.com/t/font_1477980_cibtf6bi5zj.woff') format('woff'),
  url('http://at.alicdn.com/t/font_1477980_cibtf6bi5zj.ttf') format('truetype'),
  url('http://at.alicdn.com/t/font_1477980_cibtf6bi5zj.svg#iconfont') format('svg');
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
        position: fixed;
        top: 0;
        left: 0;
        width: 37.5rem;
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
    #lists>li:first-child{
        margin-top: 5rem;
    }
    #top_two{
        padding: 2rem 1.5rem ;
        font-size: 1.17rem;
    }
    #red_span{
        color: red;
    }
    .right_blue{
        float: right;
        color: #3190e8;
    }
    .topsmall{
        position: relative;
        bottom: 0.3rem;
        right: 0.5rem;
    }
    #bottom_one{
        color: #999;
        margin: 0.5rem 1.8rem;
        line-height: 3rem;
        background-color: #f9f9f9;
        font-size: 1rem;
    }
    #bottom_two{
        text-align: center;
        color: #333;
        margin-top: 2rem;
        line-height: 2rem;
        font-size: 1.2rem;
    }
    #last{
        position: fixed;
        bottom: 0;
        left: 0;
        font-size: 1.6rem;
        color: #555;
        line-height: 4.6rem;
        width: 37.5rem;
        background-color: #fff;
    }
    #last>span{
        display: block;
        float: left;
        width: 50%;
        text-align: center;
    }
    #lists{
        padding: 0 1.8rem;
    }
    .list{
        padding: 2rem 1.2rem;
        margin-top: 1rem;
        border-top: 3px solid #ccc;
        border-radius: 0.8rem;
        padding-top: 0;
        background-color: #fff;
        height:8rem;
    }
    .xuxian{
        border-top: 3px dashed #ccc;   
    }
    .list_left{
        float: left;
        width: 30%; 
    }
    .list_center{
        float: left;
        width: 50%;
        margin-top: 2rem;
    }
    .list_right{
        float: left;
        width: 20%;
        margin-top: 2rem;
        text-align: center;
        color: #ccc;
        font-size: 7rem;
    }
    
    .list_money{
        padding-top: 2rem;
        color: #ccc;
        font-size: 1.875rem;
        font-weight: 700;
    }
    .list_money_num{
        font-size: 3.5rem;
    }
    .man_money{
        color: #999;
        font-size: 1rem;
        line-height: 1.3rem;
        margin-left: 0.5rem;
        margin-top: 1rem;
    }
    .fenxiang{
        color: #666;
        font-size: 1.6rem;
        line-height: 2.1rem;
    }
    .data{
        color: #999;
        font-size: 1rem;
        line-height: 1.28rem;
    }
    .phone{
        color: #999;
        font-size: 1rem;
        line-height: 1.28rem;
    }
</style>