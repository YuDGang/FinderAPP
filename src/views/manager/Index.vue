<template>
  <!-- 后台管理总页面 -->
  <div class="manager">
    <!-- 用于接受管理页面，租赁页面，订单页，我的页面 -->
    <router-view></router-view>
    <van-tabbar route active-color="#1659a0">
      <van-tabbar-item icon="https://cdn4.iconfinder.com/data/icons/shopping-e-commerce-1/128/Trust-Handshake-Partner-Deal-64.png" to="/manager/home">租赁</van-tabbar-item>
      <van-tabbar-item icon="https://cdn4.iconfinder.com/data/icons/shopping-e-commerce-1/128/Special-Top-List-64.png" to="/manager/order">订单</van-tabbar-item>
      <van-tabbar-item icon="https://cdn4.iconfinder.com/data/icons/shopping-e-commerce-1/128/Tag-Price-Label-64.png" to="/manager/user">我的</van-tabbar-item>
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