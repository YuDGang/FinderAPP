<template>
  <div class="user">
    <div class="header">
      <div class="photo">
        <img src="../../assets/user1.jpg" alt=""/>
      </div>
      <div class="name">{{info.name}}</div>
    </div>
    
    <van-cell title="常用地址" is-link to="/manager/address" />
    <van-cell title="所有订单" is-link to="/manager/order" />

    <div class="btn" @click="logoutHandler">
      切换账号
    </div>
  </div>
</template>
<script>
import {mapState, mapActions} from 'vuex'
export default {
  methods:{
    ...mapActions('user',['logout']),
    toAddressHandler(){
      // this.$router.push({path:'/manager/address'})
    },
    logoutHandler(){
      this.logout()
      .then(()=>{
        this.$router.push({path:'/login'})
      })
    }
  },
  computed:{
    ...mapState("user",["info"])
  }
}
</script>

<style scoped>
.header {
  padding-top: 46px;
  text-align: center;
  background: url('../../assets/userup.jpg') center center no-repeat;
  background-size: 420px auto;
  margin-bottom: 2em;
}

.header .photo {
  margin: 0 auto;
  width: 10em;
  height: 10em;
  border-radius: 50%;
  box-sizing: border-box;
  border:2px solid #1659a0;
  overflow:hidden;
  padding: 0em;
}
.header .name {
  line-height: 3em;
  font-size: 16px;
  color: #ffffff;

}
.header .photo img {
 width: 100%;
 border-radius: 50%;
}

.btn {
  width: 90%;
  margin: 1em auto;
  line-height: 3em;
  text-align: center;
  border: 1px solid #1659a0;
  border-radius: 1.5em;
}

</style>