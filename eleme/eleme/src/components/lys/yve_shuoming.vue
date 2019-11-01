<template>
    <div id="SM">
          <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
              <span id="login_title_center">余额问题</span>
          </div>
          <div id="text">
              <div :key="i" v-for="(v,i) in title">
                  <p class="title" v-text="v"></p>
                  <p class="conent" v-text="conent[i]"></p>
              </div>
              
          </div>
    </div>
   
</template>

<script>
export default {
    name:"yve_shuoming",
    data(){
        return{
            title:["Q1: 使用余额的条件","Q2: 余额可以怎么用？","Q3:我要如何提现？","Q4:为什么会提现失败？"],
            conent:["为了保护账户安全，使用余额前必须先绑定手机号。","余额可以在饿了么平台上提现，当余额大于等于待支付金额时可以在支持在线支付的商家中进行消费。提现功能将于2016年12月25日00:00全面开放。","余额可以在饿了么平台上提现，当余额大于等于待支付金额时可以在支持在线支付的商家中进行消费。提现功能将于2016年12月25日00:00全面开放。","可能原因有：您的姓名、开户行、银行卡号等信息不匹配；您当日的提现次数和金额超过限制；您的账户存在异常，被风控拦截。"]

        }
    },
    methods:{
        router1(){
            this.$router.push({
                 name:"yve",
                 path:'/yve'
            })
        }
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
    #text{
        padding: 0 1.1rem;
    }
    .title{
        font-size: 1.65rem;
        line-height: 4.6rem;
        color: #333;
    }
    .conent{
        font-size: 1.4rem;
        color: #666;
        line-height: 2.3rem;
    }
</style>