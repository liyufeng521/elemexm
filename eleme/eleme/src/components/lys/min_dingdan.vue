<template>
  <div id="DD">
        <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
              <span id="login_title_center">订单列表</span>
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
</style>