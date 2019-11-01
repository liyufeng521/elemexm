<template>
  <div id="app">
      <div id="fix" @click="clk()"></div>
      <div id="login_title">
            <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
            <span id="login_title_center">兑换红包</span>
        </div>
      <img src="../lys/img/gogo.png" alt="" id="both">
  </div>
</template>

<script>
export default {
    name:'tuijian_jiang',
    data(){
        return{
            
        }
    },
    methods:{
        router1(){
             this.$router.push({
                 path:'/youhuui',
                 name:'youhui'
             });
        },
        clk(){
            alert("请在饿了么APP中打开");
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
    #both{
        width: 37.5rem;
    }
    #fix{
        width: 37.5rem;
        height: 9rem;
        position: fixed;
        top: 30rem;
        left: 0;
    }
</style>