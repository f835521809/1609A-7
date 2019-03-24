<template>
  <div class="wrap">
    <header>
      <image src="/static/images/ren.png" lazy-load="false"></image>
      <p>176****0325</p>
    </header>
    <ul>
        <li>
          <div>
            <span><img src="../../../static/images/money.png" /></span>
            <span>我的钱包</span>
          </div>
          <b>></b>
        </li>
        <li>
          <div>
            <span><img src="../../../static/images/ka.png" /></span>
            <span>我的卡券</span>
          </div>
          <b>></b>
        </li>
        <li @click="goSignList">
          <div>
            <span><img src="../../../static/images/lv.png" /></span>
            <span>我的行程</span>
          </div>
          <b>></b>
        </li>
    </ul>

    <div class="footer">
      <p>切换账号</p>
    </div>
    <!-- <div class="phone" v-if="showPhoneDialog">
      <p>为了更好的使用我们的服务，我们需要获取你的手机号码</p>
      <button open-type="getPhoneNumber" @getphonenumber="getPhoneNumber">允许获取手机号</button>
    </div> -->
  </div>
</template>

<script>
import {getLocation, getAuth} from '@/utils/index.js'
import {mapState, mapMutations} from 'vuex'
export default {
  data () {
    return {
      showPhoneDialog: true
    }
  },
  computed: {
    ...mapState({
      info: state=>state.info
    })
  },
  methods: {
    getPhoneNumber(e){},
     goSignList(){
       wx.navigateTo({ url: '/pages/sign/list/main' });
    }
  },
  onShow() {
    if (!this.info.phone){
      this.showPhoneDialog = false;
    }
  }
}
</script>

<style lang="scss" scoped>
header{
  background: #F4F6F9;
  width: 100%;
  height: 400rpx;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  image{
    width: 200rpx;
    height: 200rpx;
  }
}
ul {
   width: 100%;
   height: 100%;
   margin-top: 30px;
   li{
    display: flex;
    justify-content: space-between;
    height: 100rpx;
    line-height: 100rpx;  
    padding:  0 30rpx;
    span{
       img {
        width: 35rpx;
        height: 35rpx; 
      }
    } 
    span{
       margin-left: 35rpx;
    }
   }
}

.footer{
  width: 100%;
   height: 100rpx;
   line-height: 100rpx;
   background: red;
   position: fixed;
   bottom:0;
   text-align: center;
}
.phone{
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0, .3);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  p{
    width: 60%;
    background: #fff;
  }
  button{
    width: 60%;
  }
}
</style>