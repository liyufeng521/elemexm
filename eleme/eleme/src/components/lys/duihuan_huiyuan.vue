<template>
  <div id="DHHY">
        <div id="login_title">
            <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
            <span id="login_title_center">兑换会员</span>
        </div>
        <p id="ppp">
            <span>成功兑换后将关联到当前账号: </span> 
            <span id="user">{{user}}</span>
        </p>
        <input type="text" placeholder="请输入10位卡号">
        <input type="text" placeholder="请输入6位卡密">
        <button id="DW_btn">兑换</button>
        <div id="tishi_title"><span>————温馨提示————</span></div>
        <div id="tishi">
            <p>新兑换的会员服务，权益以「会员说明」为准。</p>
            <p>月卡：30次减免配送费。</p>
            <p>季卡：90次减免配送费。</p>
            <p>年卡：360次减免配送费。</p>
            <p>＊仅限蜂鸟专送订单，每日最多减免3单，每单最高减免4元（一个月按31天计算）</p>
        </div>
  </div>
</template>
<p data-v-3e3dbf9c="">新兑换的会员服务，权益以「会员说明」为准。</p>
<p data-v-3e3dbf9c=""><b data-v-3e3dbf9c="">30次</b>减免配送费。</p>
<p data-v-3e3dbf9c="">＊仅限蜂鸟专送订单，每日最多减免3单，每单最高减免4元（一个月按31天计算）</p>
<script>
export default {
    name:'duihuan_huiyuan',
    data(){
        return{
            user:"123"
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

<style>
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
    #ppp{
        color: #666;
        font-size: 1.4rem;
        padding-left: 1.6rem;
        line-height: 4.6rem;
    }
    #ppp>#user{
        color: #333;
        font-weight: 500;
    }
    #DHHY>input{
        width: 37.5rem;
        height: 4.7rem;
        padding-left: 1.6rem;
        background-color: #fff;
        color: #999;
        font-size: 1.6rem;
        margin-top: 1px;
    }
    #DW_btn{
       width: 35rem;
       height:4.1rem;
       color: #fff; 
       border: none;
       margin: 1.6rem 1.6rem 0 1.6rem; 
       border-radius: 0.5rem;
       font-size: 1.64rem;
    }
    #tishi{
        padding-left: 4.7rem;
        color: #aaa;
        line-height: 1.84rem;
        font-size: 1.17rem;
        
    }
    #tishi_title{
        text-align: center;
        margin-top: 2rem;
        margin-bottom: 1.4rem;
        color: #aaa;
        font-size: 1.52rem;
        line-height: 2rem;
    }

</style>