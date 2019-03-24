<template>
  <div class="wrap">
    <header>
      <span @click="updateState({'active':index})" v-for="(item,index) in type" :key="index" :class="active===index?'active':''">{{item}}</span>
    </header>
    <mySign :list="list" ></mySign>
  </div>
</template>


<script>
import mySign from "@/components/mySign.vue"
import {mapState,mapMutations,mapActions} from "vuex";

  export default {
      data(){
        return{
          active:0,
          type:["全部","未开始","已打卡","已放弃"]
        }
      },
      computed:{
        ...mapState({
          active:state=>state.sign.active,
          // list :state=>state.sign.list
        })
      },
      methods: {
        ...mapMutations({
          updateState:"sign/updateState"
        }),
        ...mapActions({
          getList:"sign/getList"
        })
      },
      components:{
         mySign
      },
      onShow(){
        this.getList();
      }
  }
</script>

<style lang="scss" scoped>
  .wrap{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    header{
        width: 100%;
        height: 100rpx;
        line-height: 100rpx;
        border-bottom: 5px solid #f2f2f2;
        display: flex;
        span{
          flex: 1;
          text-align: center
        }
         .active{
          color:deepskyblue;
          border-bottom: 1px solid deepskyblue;
        }
    }
  }
</style>
