<template>
  <div  class="wrap">
      <div class="nav">
        <img src="../../../static/images/my.png" alt="">
        <p>188********</p>
      </div>
      <div class="face">
        <p @click="mysign"><span><img src="../../../static/images/job.png" alt="">我的面试</span><span>》</span></p>
      </div>  
      <div class="phone">
        <button open-type="getPhoneNumber" bindgetphonenumber="getPhoneNumber">允许获取手机号</button>
        <button open-type="getUserInfo" bindgetuserinfo="getUserInfo">允许获取用户信息</button>
      </div>
  </div>
</template>

<script>
import {getLocation, getAuth} from '@/utils/index.js'
import {mapState, mapMutations} from 'vuex'

export default {
  data () {
    return {
        showPhoneDialog:false
    }
  },

  computed: {
    ...mapState({
      info: state=>state.info
    })
  },



  methods: {
      // getPhoneNumber(e){
      //     console.log("getNumber..........",e)
      // },
      // getUserInfo(e){
      //     console.log("getUserInfo..........",e)
      // },
      mysign(){
        wx.navigateTo({ url: '/pages/sign/list/main' });
      }
  },

  onShow() {
    console.log(this.info)
    if(this.info.phone){
        this.showPhoneDialog=true
    }
  },
} 
</script>

<style lang="scss" scoped>

  .phone{
    // display: none;
    margin-top: 100rpx;
    button{
      width: 80%;
      background: rgb(30, 255, 0);
      color:#fff;
    }
  }
  .nav{
    width: 100%;
    height: 200px;
    text-align: center;
    background: blanchedalmond;
    img{
      width: 50px;
      height: 50px;
      margin: 50px 0;
    }
  }
  .face img{
       width:30px;
      height:30px;
  }
  .face p{
    width: 100%;
    height: 80rpx;
    line-height: 80rpx;
    display: flex;
    justify-content: space-between;
  }
</style>
