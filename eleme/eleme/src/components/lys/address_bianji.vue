<template>
  <div id="address_XG">
        <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
              <span id="login_title_center">编辑地址</span>
              <span id="delate" v-text="gai_text" @click="genggai()"></span>
        </div>
        <ul id="lists">
            <li v-for="(v,i) in address_list" :key="i">
                <p>{{v.name}}</p>
                <p>{{v.phone}}</p>
                <span class="el-icon-close del_list" @click="del(i)"></span>
            </li>
        </ul>
        <p id="add" @click="router2()"><span>新增地址</span><span class="el-icon-arrow-right
 add_i"></span></p>
         <!-- 弹出框 -->
           <div id="mask">
               <div id="kuang">
               <span class="el-icon-warning-outline kuang_i"></span> 
               <p v-text="message"></p>
               <button @click="knone()">确认</button>
               </div>
           </div>
  </div>
</template>

<script>
export default {
    name:"address_bianji",
    data(){
        return{
            gai_text:"编辑",
            data:{},
            address_list:[],
            message:""
        }
    },
    created(){
        this.data=this.$route.query.data;
        console.log(this.data);
        this.getdizhi();
    },
    methods:{
        genggai(){
            // var listobj = document.getElementsByClassName("del_list");
            if(this.gai_text=="编辑"){
                // for(var j=0;j<this.listobj.length;j++){
                //     listobj[j].style.display="block"; 
                // } 
                $(".del_list").css("display","block");
                this.gai_text="完成"
            }else{
                this.gai_text="编辑";
                $(".del_list").css("display","none");
            }
        },
        router1(){
            this.$router.push({
        path:'/zhanghu',
        name:'zhanghu',
        query:{
         data:this.data,
        }
      })
    // this.$router.go(-1);
        },
        router2(){
            this.$router.push({
                path:'/address_add',
                name:'address_add',
                query:{
                    data:this.data,
                }
            })
        },
        getdizhi(){
            const api = "https://elm.cangdu.org/v1/users/"+this.data.user_id+"/addresses";
            this.$http({
                url:api,
                method:"get",
                withCredentials:true,
                data:{
                    
                }
            }).then(res=>{
                console.log(res);
                this.address_list=res.data;
            })
        },
        del(i){
            const api = "https://elm.cangdu.org/v1/users/"+this.data.user_id+"/addresses/"+this.address_list[i].id;
            this.$http({
                url:api,
                method:"delete",
                withCredentials:true,
                data:{
                    user_id:this.data.user_id,
                    address_id:this.address_list[i].id
                }
            }).then(res=>{
                this.message=res.data.success;
                this.getdizhi();
                this.kshow();
            })
        },
        kshow(){
            $("#mask").css("display","block");
        },
        knone(){
            $("#mask").css("display","none");
        }
    }
}
</script>

<style scoped>
/* 弹出框 */
#mask{
    width: 37.5rem;
    height: 66.7rem;
    position: fixed;
    top: 0;
    left: 0;
    background-color:rgba(0,0,0,0);
    display: none;
}
#kuang{
    width: 28rem;
    margin: 0 auto;
    margin-top: 12rem;
    text-align: center;
    background-color: #fff;
    border-radius: 1rem;
    overflow: hidden;
}
.kuang_i{
    font-size: 7rem;
    margin-top: 2rem;
    color: #fe6d47;
}
#kuang>p{
    color: #333;
    font-size: 1.6rem;
    margin-top: 2rem;
}
#kuang>button{
    width: 28rem;
    height: 4rem;
    background-color: #4cd964;
    color: #fff;
    font-size: 1.875rem;
    margin-top: 2rem;
    border: none;
}

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
    #delate{
        float: right;
        color: #fff;
        margin-top: 1.5rem;
        margin-right: 1rem;
    }
    #add{
        margin-top: 1rem;
        color: #333;
        font-size: 1.64rem;
        background-color: #fff;
        padding: 0.5rem 1rem;
        line-height: 3.2rem;
    }
    .add_i{
        float: right;
        line-height: 3.2rem;
    }
    #lists>li{
        position: relative;
        background-color: pink;
        margin-top: 1rem;
    }
    .del_list{
        position: absolute;
        top: 0.5rem;
        right: 2rem;
        margin-top: 1rem;
        display: none;
    }
    #lists>li>p{
        line-height: 2rem;
    }
</style>