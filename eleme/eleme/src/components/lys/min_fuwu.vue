<template>
  <div id="FW">
       <div id="login_title">
            <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
            <span id="login_title_center">服务中心</span>
        </div>
        <div id="kefu">
            <div id="kefu_left">
                <i class="iconfont kefu_i_one">&#xe62e;</i>
                <span class="kefu_span">在线客服</span>
            </div>
            <div id="kefu_right">
                <i class="iconfont kefu_i_two">&#xe601;</i>
                <span class="kefu_span">在线客服</span>
            </div>
        </div>
        <div id="list_one">热门问题</div>
        <ul id="lists">
            <li v-for="(v,i) in keys" :key="i" @click="getNext(v)">
                  <span v-text="lists[v]"></span> 
                <i class="el-icon-arrow-right"></i>
            </li>
        </ul>
  </div>
</template>

<script>
export default {
    name:'fuwu',
    data(){
        return{
            choose:"0",
            keys:[],
            lists:{}
        }
    },
    created(){
        this.gett();
    },
    methods:{
        gett(){
             const api = "https://elm.cangdu.org/v3/profile/explain";
        this.$http({
            url:api,
            method:"get",
            withCredentials:true,
        }).then(res=>{
            console.log(res.data);
            this.lists = res.data;
            for(var key in res.data){
                if(key.indexOf("Caption") !=-1){
                    this.keys.push(key);
                } 
            }
            console.log(this.lists);
            console.log(this.keys)
        })
        },
        getNext(i){
            this.$router.push({
                path:'/fuwu_text',
                name:'fuwu_text',
                query:{
                    data:this.lists,
                    mess:i
                }
            })
        },
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
@font-face {
  font-family: 'iconfont';  /* project id 1477980 */
  src: url('http://at.alicdn.com/t/font_1477980_bi3ro498y19.eot');
  src: url('http://at.alicdn.com/t/font_1477980_bi3ro498y19.eot?#iefix') format('embedded-opentype'),
  url('http://at.alicdn.com/t/font_1477980_bi3ro498y19.woff2') format('woff2'),
  url('http://at.alicdn.com/t/font_1477980_bi3ro498y19.woff') format('woff'),
  url('http://at.alicdn.com/t/font_1477980_bi3ro498y19.ttf') format('truetype'),
  url('http://at.alicdn.com/t/font_1477980_bi3ro498y19.svg#iconfont') format('svg');
}
.iconfont{
    font-family:"iconfont" !important;
    font-size:16px;font-style:normal;
    -webkit-font-smoothing: antialiased;
    -webkit-text-stroke-width: 0.2px;
    -moz-osx-font-smoothing: grayscale;
    }
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
    #kefu{
        color: #333;
        height: 8.84rem;
        margin-top: 5rem;
    }
    #kefu_left{
        text-align: center;
        width: 18.75rem;
        float: left;
        background-color: #fff;
        margin-bottom: 1px;
    }
    #kefu_right{
        text-align: center;
        width: 18.67rem;
        float: left;
        box-sizing: border-box;
        margin-left: 1px;
        background-color: #fff; 
    }
    .kefu_i_one,.kefu_i_two{
        display: block;
        margin-top: 2rem;
        font-size: 2.5rem;
    }
    .kefu_i_one{
        color: orange;
    }
    .kefu_i_two{
        color: green;
    }
    .kefu_span{
        color: #666;
        display: block;
        font-size: 1.4rem;
        margin-top: 1rem;
        margin-bottom: 2rem;
    }
    #list_one,#lists>li{
        padding: 0 1.64rem;
        line-height:4.7rem;
        font-size: 1.4rem;
        color: #333;
        margin-top: 1px;
        background-color: #fff;
    }
    #list_one{
        font-size: 1.76rem;
        line-height: 7rem;
    }
    #lists>li>i{
        float: right;
        line-height: 4.7rem;
        font-weight: 600;
    }
</style>