<template>
  <div id="zhanghu">
      <div id="login_title">
              <span class="el-icon-arrow-left" id="login_title_i" @click="router1()"></span>
              <span id="login_title_center">账户信息</span>
        </div>
        <ul id="zhanghao_message">
          <li id="zhanghu_first">
            <span class="zhanghu_left">头像</span> 
            <span class="zhuanghu_right el-icon-arrow-right"></span>
            <span class="iconfont actor">&#xe67d;</span>
            <el-upload
  class="avatar-uploader"
  action="https://jsonplaceholder.typicode.com/posts/"
  :show-file-list="false"
  :on-success="handleAvatarSuccess"
  :before-upload="beforeAvatarUpload">
  <img v-if="imageUrl" :src="imageUrl" class="avatar">
   <i v-else class="el-icon-plus avatar-uploader-icon"></i>
</el-upload>
          </li>
          <li @click="router('user')">
            <span class="zhanghu_left">用户名</span>
            <span class="zhuanghu_right el-icon-arrow-right
"></span>
            <span v-text="data.username" id="username"></span>
          </li>
          <li @click="router('address')">
            <span class="zhanghu_left">收货地址</span>
            <span class="zhuanghu_right el-icon-arrow-right
"></span>
          </li>
          <p class="zhanghu_text">账号绑定</p>
          <li @click="kshow()">
            <span class="el-icon-mobile-phone phone_i"></span>
            <span class="zhanghu_left">手机</span>
            <span class="zhuanghu_right el-icon-arrow-right
"></span>
          </li>
          <p class="zhanghu_text">安全设置</p>
          <li @click="router('password')">
            <span class="zhanghu_left">登录密码</span>
            <span class="zhuanghu_right el-icon-arrow-right
"></span>
 <span id="xiugai">修改</span>
          </li>
        </ul>
      <div id="one"><input type="button" @click="kshow2()" value="退出登录" id="tui_btn"></div>
       <!-- 弹出框 -->
           <div id="mask">
               <div id="kuang">
               <span class="el-icon-warning-outline kuang_i"></span> 
               <p v-text="'请在手机APP中设置'"></p>
               <button @click="knone">确认</button>
               </div>
           </div>
           <div id="mask2">
               <div id="kuang2">
               <span class="el-icon-warning-outline kuang_i2"></span> 
               <p v-text="'是否退出登录'"></p>
               <button @click="knone2()">再等等</button>
               <button @click="knone2(true)">确认退出</button>
               </div>
           </div>
  </div>
</template>

<script>
export default {
  name:'zhanghu',
  data(){
    return{
      data:{},
      bol:true,
      imageUrl: ''
    }
  },
  created(){
    console.log(this.$route.query.data);
   this.data = this.$route.query.data;
   
  },
  methods:{
    close(){
      const api = "https://elm.cangdu.org/v2/signout";
      this.$http({
        url:api,
        method:"get",
        withCredentials:true,
      }).then(res=>{
        console.log(res.data);
        if(this.bol){
         this.router1();
        }
      })
    },
    router1(){
      this.$router.push({
        path:'/minindex',
        name:'minindex'
      });
    },
    router(i){
      if(i=="user"){
        this.$router.push({
          path:'/user_xiugai',
          name:'user_xiugai'
        })
      }else if(i=="address"){
        this.$router.push({
          path:'/address_bianji',
          name:'address_bianji',
          query:{
            data:this.data,
          }
        })
      }else if(i=="phone"){
         alert("error");
      }else if(i=="password"){
        this.$router.push({
          path:'/password_reset',
          name:'password_reset'
        })
      }
    },
     handleAvatarSuccess(res, file) {
        this.imageUrl = URL.createObjectURL(file.raw);
      },
      beforeAvatarUpload(file) {
        const isJPG = file.type === 'image/jpeg';
        const isLt2M = file.size / 1024 / 1024 < 2;

        if (!isJPG) {
          this.$message.error('上传头像图片只能是 JPG 格式!');
        }
        if (!isLt2M) {
          this.$message.error('上传头像图片大小不能超过 2MB!');
        }
        return isJPG && isLt2M;
      },
        kshow(){
            $("#mask").css("display","block");
        },
        knone(){
            $("#mask").css("display","none");
        },
        kshow2(){
            $("#mask2").css("display","block");
        },
        knone2(i){
          if(i){
            this.close();
          }
            $("#mask2").css("display","none");
        }
  },
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

#mask2{
    width: 37.5rem;
    height: 66.7rem;
    position: fixed;
    top: 0;
    left: 0;
    background-color:rgba(0,0,0,0);
    display: none;
}
#kuang2{
    width: 28rem;
    margin: 0 auto;
    margin-top: 18rem;
    text-align: center;
    background-color: #fff;
    border-radius: 1rem;
    overflow: hidden;
}
.kuang_i2{
    font-size: 7rem;
    margin-top: 2rem;
    color: #fe6d47;
}
#kuang2>p{
    color: #333;
    font-size: 1.6rem;
    margin-top: 2rem;
}
#kuang2>button{
    width: 7rem;
    height: 3rem;
    background-color: #4cd964;
    color: #fff;
    font-size: 1.3rem;
    margin-top: 2rem;
    border: none;
    border-radius: 0.2rem;
}

@font-face {
  font-family: 'iconfont';  /* project id 1477980 */
  src: url('http://at.alicdn.com/t/font_1477980_2buov3gi6du.eot');
  src: url('http://at.alicdn.com/t/font_1477980_2buov3gi6du.eot?#iefix') format('embedded-opentype'),
  url('http://at.alicdn.com/t/font_1477980_2buov3gi6du.woff2') format('woff2'),
  url('http://at.alicdn.com/t/font_1477980_2buov3gi6du.woff') format('woff'),
  url('http://at.alicdn.com/t/font_1477980_2buov3gi6du.ttf') format('truetype'),
  url('http://at.alicdn.com/t/font_1477980_2buov3gi6du.svg#iconfont') format('svg');
}
  .iconfont{
    font-family:"iconfont" !important;
    font-size:16px;font-style:normal;
    -webkit-font-smoothing: antialiased;
    -webkit-text-stroke-width: 0.2px;
    -moz-osx-font-smoothing: grayscale;}
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
    #min_min{
      margin-top: 1px;
      background-color: #3190e8;
      position: relative;
    }
    #zhanghao_message>li{
      color: #333;
      padding: 0.7rem;
      background-color: #fff;
      font-size: 1.4rem;
      line-height: 3.2rem;
      margin-top: 2px;
    }
    #zhanghao_message>#zhanghu_first{
      margin-top: 1rem;
      line-height:7.26rem; 
      position: relative;
    }
    .zhanghu_text{
      color: #666;
      font-size: 1.17rem;
      padding: 0.93rem;
    }
    .zhuanghu_right{
      float: right;
      line-height: 3.2rem;
      font-size: 1.8rem;
    }
    #zhanghu_first>.zhuanghu_right{
      line-height: 7.26rem;
    }
    #xiugai{
      float: right;
      margin-right: 0.1rem;
      font-size:1.64rem;
      color: #999; 
    }
    #tui_btn{
      width:36rem;
      height: 3.44rem;
      font-size: 1.4rem;
      background-color: #d8584a;
      color: #fff;
      margin-top: 3rem;
      border-radius: 0.5rem; 
    }
    .actor{
      font-size: 4rem;
      float: right;
      margin-right: 0.5rem;
      color: #3190e8;
    }
    .phone_i{
      color: #3190e8;
    }
    #one{
      text-align: center;
    }
    #username{
      float: right;
      margin-right: 1rem;
    }
    /* 文件图片选取 */
    .avatar-uploader{
      position: absolute;
      width: 37.5rem;
      height: 7.2rem;
      top: 0;
      left: 0;
    }
     .avatar-uploader .el-upload {
    /* border: 1px dashed #d9d9d9; */
    width: 37.5rem;
    height: 7.2rem;
    cursor: pointer;
    position: relative;
    overflow: hidden;
  }
  .avatar-uploader .el-upload:hover {
    border-color: #409EFF;
  }
  .el-icon-plus:before{
    color: rgba(0, 0, 0, 0);
  }
  .avatar-uploader-icon {
    font-size: 28px;
    color: #8c939d;
    width: 37.5rem;
    height: 7.2rem;
    line-height: 178px;
    text-align: center;
    position: absolute;
    top: 0;
    left: 0;
  }
  .avatar {
   height: 4rem;
   width: 4rem;
   position: absolute;
   top: 2.3rem;
   right: 3rem;
   display: block;
   border-radius: 50%;
  }
</style>