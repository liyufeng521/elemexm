<template>
  <div>
       <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i" @click="routergo()"></span>
              <span id="login_title_center">优惠券说明</span>
        </div>
      <p class="title">Q1: 什么是商家代金券？</p>
      <p class="conent">商家代金券是指由商家自己发放代金券，只限在指定的商家使用，可根据条件抵扣相应金额。</p>
      <p class="title">Q2: 怎么获得商家代金券？</p>
      <p class="conent">进入有「进店领券」或「下单返券」标示的商家即有机会获得代金券。</p>
      <p class="conent">「下单返券」需要在指定商家完成满足返券金额要求的订单后才会返还，代金券可在下次下单时使用。</p>
      <p class="title">Q3: 商家代金券使用条件</p>
      <p class="conent">商家代金券仅限在指定商家使用</p>
      <p class="conent">商家代金券仅限在线支付使用</p>
      <p class="conent">每个订单只能使用一张商家代金券，不可与其他代金券叠加使用</p>
  </div>
</template>
<script>
export default {
    name:'jinjuan_shuoming',
    methods:{
        routergo(){
            this.$router.push({
                name:'youhui',
            });
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
    .conent_first{
        color: #666;
        padding: 0 1.2rem;
        line-height: 2rem;
        font-size: 1.6rem;
    }
    .title{
        color: #333;
        font-size: 1.64rem;
        margin: 0.8rem 0;
        padding: 0 1.2rem;
        font-weight: 400;
    }
    .conent{
        color: #666;
        font-size: 1.4rem;
        line-height: 2rem;
        padding: 0 1.2rem;
        font-weight: 300;
    }
</style>