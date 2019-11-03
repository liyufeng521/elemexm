<template>
<div id="app">
  <p id="top_two"><span>有<span id="red_span">{{mess.length}}</span>个红包即将到期</span> <span class="right_blue" @click="router2()">红包说明</span><span class="iconfont right_blue topsmall">&#xe64d;</span></p>
        <ul id="lists">
            <li class="list" v-show="mess_bol" :key="i" v-for="(v,i) in mess">
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
                <span class="list_right">剩3日</span>
            </li>
        </ul>
        <p id="bottom_one">限品类：快餐便当、特色菜系、小吃夜宵、甜品饮品、异国料理</p>
        <p id="bottom_two" @click="router3()"><span>查看历史红包</span><span class="el-icon-arrow-right"></span></p>
        <p id="last"><span id="last_left" @click="router4()">兑换红包</span><span id="last_right" @click="router5()">推荐有奖</span></p>
        </div>
</template>

<script>
export default {
    name:"hongbao",
    data(){
        return{
             data:{},//传过来的信息
            mess:"",//请求的信息
            mess_bol:false,
            lists:[],
            amount:""
        }
    },
     created(){
        this.data=this.$route.query.data;
        console.log(this.data);
        this.getmessage();
    },
    methods:{
         
        getmessage(){
            const api = "https://elm.cangdu.org/promotion/v2/users/1/hongbaos?limit=20&offset=0"
            this.$http({
                url:api,
                method:"get",
            }).then(res=>{
                console.log(res);
                this.mess=res.data;
                this.mess_bol=true;
            })
        },
        router2(){
            this.$router.push({
                path:'/hongbao_shuoming',
                name:"hongbao_shuoming"
            })
        },
        router3(){
            this.$router.push({
                path:'/hongbao_history',
                name:'hongbao_history'
            })
        },
        router4(){
            this.$router.push({
                path:'/hongbao_duihuan',
                name:'hongbao_duihuan'
            })
        },
        router5(){
             this.$router.push({
                path:'/tuijian_jiang',
                name:'tuijian_jiang',
                query:{
                    
                }
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
        border-top: 3px solid #ff5340;
        border-radius: 0.8rem;
        padding-top: 0;
        background-color: #fff;
        height:8rem;
    }
    .xuxian{
        border-top: 3px dashed #ff5340;   
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
        color: #ff5340;
        font-size: 1.75rem;
    }
    
    .list_money{
        padding-top: 2rem;
        color: #ff5340;
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