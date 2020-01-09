<template>
  <!-- 后台管理总页面 -->
  <div class="manager">
    <!-- 用于接受管理页面，首页，订单页，我的页面 -->
    <router-view></router-view>
    <van-tabbar route active-color="#1659a0">
      <van-tabbar-item icon="https://s4.aconvert.com/convert/p3r68-cdx67/a5xus-r4n8f.svg" to="/manager/home">首页</van-tabbar-item>
      <van-tabbar-item icon="https://s4.aconvert.com/convert/p3r68-cdx67/aspp6-i9qnj.svg" to="/manager/order">订单</van-tabbar-item>
      <van-tabbar-item icon="https://s4.aconvert.com/convert/p3r68-cdx67/att55-putjg.svg" to="/manager/user">我的</van-tabbar-item>
    </van-tabbar>
  </div>
</template>
<script>
import {mapState,mapActions} from 'vuex'
export default {
  created(){
    
  },
  computed:{
    ...mapState('user',['info'])
  },
  methods:{
    
  }
}
</script>