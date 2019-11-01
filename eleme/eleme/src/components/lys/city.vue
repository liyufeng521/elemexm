<template>
  <div id="both">
      <div id="title">
          <span id="title_left">ele.me</span>
          <span class="el-icon-user-solid" id="title_right"></span>
      </div>
      <div id="help_text">
          <span id="help_text_left">当前定位城市</span>
          <span id="help_text_right">定位不准时,请在城市列表中选择</span>
      </div>
      <div id="guess" :v-if = "show==3" @click = "next()">
          <span id="guess_name" v-text="this.guessCity.name"></span>
          <span class="el-icon-arrow-right" id="guess_i"></span>
      </div>
      <div id="hot" :v-if = "show==3">
          <p id="hot_title">热门城市</p>
            <ul id="hot_citys">
                <li :key="i" v-for="(v,i) in hotCity" v-text="v.name" @click ="next()"></li>
            </ul>
      </div>
        <div id="gr">
          <ul class="group" :key="i" v-for="(v,i) in arr" :v-if ="show==3">
              <p v-text="v" class = "group_title"> </p>
             <!-- <span v-if="i==0" id ="text_tishi">按字母排序</span> -->
              <li :key="n" v-for="(m,n) in groupCity[v]" v-text="m.name" class="group_city" @click="next()"></li>
          </ul>
      </div>
  </div>
</template>

<script>
export default {
    name:"city",
    data(){
        return{
            guessCity:{},
            hotCity:[],
            groupCity:{},
            arr:[],
            show:0,
        }
    },
    created(){
        this.getGuessCity(),
        this.getHotCitys(),
        this.getGroupCity()
    },
    methods:{
        getGuessCity(){
            const api = "https://elm.cangdu.org/v1/cities?type=guess";
            this.$http({
                url:api,
                method:"get",
                withCredentials:true,//默认为false
                data:{

                }
            }).then(res=>{//请求回来的定位城市
                console.log(res);
                this.guessCity = res.data;
                console.log(this.guessCity.name);
                this.show++;
            })
        },
        getHotCitys(){
            const api = "https://elm.cangdu.org/v1/cities?type=hot";
            this.$http({
                url:api,
                method:"get",
                data:{

                }
            }).then(res=>{//请求回来的热门城市列表
                // console.log(res);
                this.hotCity=res.data;
                this.show++;
            })
        },
        getGroupCity(){
            const api = "https://elm.cangdu.org/v1/cities?type=group";
            this.$http({
                url:api,
                method:"get",
                data:{

                }
            }).then(res=>{//请求回来的所有城市列表
                console.log(res);
                this.groupCity=res.data;
                console.log(this.groupCity);
                for (var key in res.data){ 
                    this.arr.push(key);
                    this.arr.sort();
                }
                this.show++;
                // for(var i = 0;i < this.arr.length; i++){
                //   this.groupCity[this.arr[i]]=res.data[this.arr[i]];  
                // }
                // for(var key in res.data){
                //     this.$set(this.groupCity,this.groupCity.length,key);
                // }
            })
        },
        next(){

        }
    },
    
}
</script>

<style scoped>
    /* html{
        font-size: 10px;
    } */
    #both{
        background-color: #f5f5f5;
    }
    #both>div{
        background-color:white;
    }
    #both #title{
        height: 4.57rem;
        background-color: #409EFF;
        color: white;
    }
    #title_left{
        float: left;
        font-size: 2rem;
        margin-left: 1rem;
        line-height: 4.57rem;
    }
    #title_right{
        float: right;
        margin-right: 1.5rem; 
        font-size: 2.5rem;
        line-height: 4.57rem;
    }
    #help_text{
        margin-top: 1rem;
        height: 3.36rem;
    }
    #help_text_left{
        color: #666;
        font-size: 1.3rem;
        line-height: 3.36rem;
        float: left;
        margin-left: 1rem;
    }
     #help_text_right{
        color: #9f9f9f;
        font-size: 1.11rem;
        line-height: 3.36rem;
        float: right;
        margin-right: 1rem;
    }
    #guess{
        height: 4.21rem;
        border-top: 1px solid #e4e4e4;
    }
    #guess_name{
        color: #3190e8;
        font-size: 1.758rem;
        float: left;
        margin-left: 1rem;
        line-height: 4.21rem;
    }
    #guess_i{
        color: #999;
        font-size: 2rem;
        font-weight: 1rem;
        float: right;
        margin-right: 1rem;
        line-height: 4.21rem;
    }
    #hot {
        margin-top: 2rem;

    }
    #hot_title{
        line-height: 3.66rem;
        margin-left: 1rem;
        color: #666;
        font-size: 1.28rem;
    }
    #hot_citys{
        border-top: 1px solid #e4e4e4;
    }
    #hot_citys > li{
        width: 25%;
        line-height: 4.1rem;
        border-right: 1px solid  #e4e4e4;
        border-bottom: 1px solid  #e4e4e4;
        color:#3190e8;
        float: left;
        box-sizing:border-box;
        text-align: center;
        background-color: white;
    }
    #gr{
        clear:both;
    }
    .group{
        border-top: 1px solid  #e4e4e4;
        overflow: hidden;
        border-top:1rem solid #e4e4e4;
    }
    #text_tishi{
        float:left;
        margin-left:1rem;
        color:#999;
        font-size:1.11rem;
    }
    .group_title{
        height:4rem;
        line-height: 4rem;
        margin-left: 1rem;
        color: #666;
        font-size: 1.29rem;
        border-bottom:1px solid #e4e4e4;
    }
    .group_city{
        width: 25%;
        box-sizing: border-box;
        color: #666;
        font-size: 1.4rem;
        text-align: center;
        line-height: 4.1rem;
        height: 4.1rem;
        border-right: 1px solid  #e4e4e4;
        border-bottom: 1px solid  #e4e4e4;
        float: left;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
    }
</style>