<template>
<div id="app">
    <div id="login_title">
        <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
        <span id="login_title_center">服务中心</span>
    </div>
    <p v-text="lists[mess]" id="content"></p>
</div>
   
</template>

<script>
export default {
    name:'fuwu_text',
    data(){
        return{
            mess:"",
            lists:{},
            list:[]
        }
    },
    created(){
        this.lists=this.$route.query.data;
        this.list=this.$route.query.mess.split("C");
        // console.log(this.$route.query);
        console.log(this.list);
        this.mess=this.list[0]+"Content";
    },
    methods:{
        router1(){
            this.$router.go(-1);
        }
    }

}
</script>

<style scoped>
     #login_title{
        height: 4.57rem;
        background-color: #3190e8;
        text-align: center;
        position: fixed;
        width: 37.5rem;
        top: 0;
        left: 0;
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
    #content{
        margin-top: 5rem;
        font-size: 1.7rem;
        color: #666;
        line-height: 2.3rem;
    }
</style>