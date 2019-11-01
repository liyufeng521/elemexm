<template>
  <div id="app">
      <p id="top_two"><span class="right_blue" @click="router(2)">商家代金券说明</span><span class="iconfont right_blue topsmall">&#xe64d;</span></p>
      <div id="center_center">
          <span class="iconfont center_i">&#xe60b;</span>
          <p id="cant">无法使用代金券</p>
          <p id="di">非客户端或客户端版本过低</p>
          <button id="JJ_btn" @click="router(1)">下载或升级客户端</button>
      </div>
  </div>
</template>

<script>
export default {
    name:'jinjuan',
    methods:{
        router(i){
            if(i==1){
                 this.$router.push({
                path:'/location',
                name:'location'
            })
            }else if(i==2){
                this.$router.push({
                path:'/jinjuan_shuoming',
                name:'jinjuan_shuoming'
            })  
            }
           
        },
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
    .right_blue{
        float: right;
        color: #3190e8;
    }
    #center_center{
        text-align: center;
        margin-top: 10rem;
    }
    .center_i{
        font-size: 8rem;
        color: #3190e8;
    }
    #cant{
       margin-top: 2rem;
       color: #666;
       font-size: 1.64rem;
       line-height: 2.16rem;       
    }
    #di{
        color: #999;
        font-size: 1.17rem;
        line-height: 1.52rem;
        margin: 0.7rem 0;
    }
    #JJ_btn{
        width: 13.5rem;
        height: 3.4rem;
        line-height: 3.4rem;
        color: #fff;
        background-color: #56d176;
        font-size: 1.52rem;
        border: none;
        border-radius: 0.5rem;
        margin-top: 0.5rem;
    }
</style>