<template>
  <div id="add">
      <div id="login_title">
            <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
            <span id="login_title_center">新增地址</span>
        </div>
        <div id="add_form">
            <input type="text" v-model="name" placeholder="请填写你的姓名">
            <input type="text" v-model="address" @click="getxinxi()"  placeholder="小区/写字楼/学校等">
            <input type="text" v-model="address_detail" placeholder="请填写详细送餐地址">
            <input type="text" v-model="phone" placeholder="请填写能够联系到你的手机号">
            <input type="text" v-model="phone_bk" placeholder="备用联系电话(选填)">
            <div><button @click="add_address()">新增地址</button></div>
        </div>
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
    name:"address_add",
    data(){
        return{
            data:{},
            user_id:"",
            address:"",
            address_detail:"",
            name:"",
            phone:"",
            phone_bk:"",
            geohash:"",
            tag:"tag",
            sex:"1",
            tag_type:"1",
            geo_xinxi:{},
            message:"",
            zhuan:false,
        }
    },
    created(){
        this.data = this.$route.query.data;
        this.user_id=this.$route.query.data.user_id;
        this.address=this.$route.query.xinxi.name;
        console.log(this.$route.query.xinxi);
        console.log(this.$route.query.name);
        console.log(this.user_id);
        console.log(this.data);
        this.geohash=this.$route.query.xinxi.geohash;
        console.log(this.geohash);
        this.name=this.$route.query.name;
        console.log(this.name);

    },
    methods:{
        router1(){
            this.$router.push({
                path:'/address_bianji',
                name:'address_bianji',
                query:{
                    data:this.data,
                }
            })
        },
        add_address(){
            const api = "https://elm.cangdu.org/v1/users/"+this.user_id+"/addresses";
            this.$http({
                url:api,
                method:"post",
                data:{
                    user_id:this.user_id,
                    address:this.address,
                    address_detail:this.address_detail,
                    geohash:this.geohash,
                    name:this.name,
                    phone:this.phone,
                    tag:this.tag,
                    sex:this.sex,
                    phone_bk:this.phone_bk,
                    tag_type:this.tag_type
                }
            }).then(res=>{
                this.message=res.data.success;
                if(this.message){
                    this.kshow();
                }else{
                    this.message="信息错误，无法添加";
                    this.kshow();
                }
                
                
            });

        },
        getxinxi(){
            this.$router.push({
                path:'/sousuo',
                name:'sousuo',
                query:{
                    data:this.data,
                    name:this.name,
                }
            })
        },
        kshow(){
            $("#mask").css("display","block");
        },
        knone(){
            this.zhuan=true;
            $("#mask").css("display","none");           
        }
    },
    watch:{
        zhuan:function(newV,oldV){
            if(newV){
                this.router1();
            }
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
    margin-top: 18rem;
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
    #add_form>input{
        width: 37.5rem;
        line-height: 3rem;
        margin-top: 2px;
        padding:1rem;
        box-sizing: border-box;
    }
    #add_form>div{
        text-align: center;
    }
    #add_form>div>button{
        margin-top: 1rem;
        width:35rem;
        line-height: 3.68rem;
        font-size: 1.4rem;
        color: #fff;
        background-color:green;
        border: none; 
        border-radius: 0.5rem;
    }
</style>