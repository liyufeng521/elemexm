<template>
  <div id="address_XG">
        <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
              <span id="login_title_center">编辑地址</span>
              <span id="delate" v-text="gai_text" @click="genggai()"></span>
        </div>
        <ul id="lists">
            <p v-text="delate"></p>
            <li v-for="(v,i) in address_list" :key="i">
                <p>{{v.name}}</p>
                <p>{{v.phone}}</p>
                <span class="el-icon-close del_list" @click="del(i)"></span>
            </li>
        </ul>
        <p id="add" @click="router2()"><span>新增地址</span><span class="el-icon-arrow-right
 add_i"></span></p>
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
    //         this.$router.push({
    //     path:'/zhanghu',
    //     name:'zhanghu',
    //     query:{
    //      data:this.data,
    //     }
    //   })
    this.$router.go(-1);
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
                this.getdizhi();
                alert(res.data.success);
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