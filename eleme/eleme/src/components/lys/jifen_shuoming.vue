<template>
    <div id="SM">
          <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
              <span id="login_title_center">积分问题</span>
          </div>
          <div id="text">
              <div :key="i" v-for="(v,i) in title">
                  <p class="title" v-text="v"></p>
                  <p class="conent" :key="n" v-for="(m,n) in conent2" v-text="m" v-if="i==0"></p>
                  <p class="conent" v-text="conent[i]"></p>
              </div>
              
          </div>
    </div>
</template>
<script>
export default {
    name:"jifen_shuoming",
    data(){
        return{
            title:["Q1: 怎么获得积分？","Q2: 积分用来做什么？","Q3: 礼品兑换很多天了还没有收到，该怎么办？","Q4: 礼品兑换中的手机充值卡兑换，怎么样进行充值，充值之前会和我电话确认嘛？"],
            conent:["每位用户每天最多可以获得2000积分，体验商家的订单和评价不会增加积分。","可以在积分商城兑换各种礼品。","礼品从兑换日起，3个工作日（周末不算）内处理发货，发货后，通常会在3个工作日左右送达。","不会，手机充值卡兑换，是直接充值到您填写的手机号上，充值之前不会和您电话确认，所以您在填写电话的时候，请确认电话是否正确。"],
            conent2:["在线支付的订单将获得订单积分奖励：","积分将在用户完成评价后获得","可获得积分=订单金额×10（即1元=10点积分）。","订单金额指实际付款金额，不包含活动优惠金额。"],

        }
    },
    methods:{
        router1(){
            this.$router.push({
                 name:"min_jifen",
                 path:'/min_jifen'
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