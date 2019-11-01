<template>
  <div id="HYSM">
        <div id="login_title">
            <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
            <span id="login_title_center">我的优惠</span>
        </div>
        <div id="conent">
            <p class="conent_first">尊敬的用户，随着会员体系逐渐完善，自2016年10月10日起，饿了么会员权益将做如下优化：
              购卡后31天内，累积享有30单减免配送费服务（每日最多3单，每单最高减免4元）。
              注：已购买的会员服务不受影响，当前会员服务失效前无法购买新卡。
            </p>
            <p class="title">Q1: 特权介绍</p>
            <p class="conent">身份标识：饿了么会员服务有效期内，享有专属皇冠标识。</p>
            <p class="conent">减免配送费： 饿了么会员卡自绑定账户之日起31天内，在「蜂鸟专送」标识商家下单，享有30次减免配送费特权，每日最多减免3单，每单最高可减4元。</p>
            <p class="conent">更多特权，敬请期待！</p>
            <p class="title">Q2: 资费介绍</p>
            <p class="conent">饿了么会员卡：20元</p>
            <p class="title">Q3: 使用说明</p>
            <p class="conent">当用户满足以下任一条件，会员服务自动失效：</p>
            <p class="conent">自绑定之日起超过31天；</p>
            <p class="conent">在31天内累计使用减免配送费的蜂鸟订单数量达到30单；</p>
            <p class="title">Q4: 购卡说明</p>
            <p class="conent">在线购买：饿了么App&gt;我的&gt;饿了么会员卡</p>
            <p class="title">Q5:温馨提示</p>
            <p class="conent">用户在当前会员服务失效前，无法购买新卡。</p>
            <p class="conent">请认准饿了么官方渠道，任何从其他第三方途径获得的会员卡，饿了么不保证其可用性。</p>
        </div>
  </div>
</template>

<script>
export default {
    name:'huiyuan_shuoming',
    data(){
        return{
           
        }
    },
    methods:{
        router1(){
            this.$router.push({
                path:'/huiyuan',
                name:'huiyuan'
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
        font-weight: 600;
    }
    .conent{
        color: #666;
        font-size: 1.4rem;
        line-height: 2rem;
        padding: 0 1.2rem;
        font-weight: 300;
    }
</style>