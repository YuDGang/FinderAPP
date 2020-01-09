<template>
<div>
    <header class="header">

 
        <video 
          id="my-video"
          class="video-js vjs-default-skin box"
          controls 
          preload="auto"
        >
            <source
                src=" https://du.hupucdn.com/ltcJ4VzrjX-sYBpRB3sQKhVYtWzL"
                type="application/x-mpegURL"
            />
        </video>
    </header>

    
    
    <!-- 内容区域 -->

      <!-- 分类 6个-->
     
      <van-grid :column-num="3">
        <van-grid-item
          v-for="value in categories"
          :key="value.id"
          :icon="value.icon"
          :text="value.name"
        />
      </van-grid>
      <!-- 产品 n个-->
      <briup-product-item 
        @click="toBuyHandler(p)"
        v-for="p in products"
        :key="p.id" 
        :data="p">
      </briup-product-item>
      <!-- /产品 -->
  
      </div>
</template>









<script>
import {get,post} from '../../http/axios';
import videojs from 'video.js'
import 'videojs-contrib-hls'
export default {
  data(){
    return {
      categories:[],
      products:[]
    }
  },
  created(){
    // 查询栏目信息
    this.loadCategories();
    // 查询产品
    this.loadProducts();
  },
  methods:{
     mounted() {
        videojs("my-video", 
            function() {
            this.play();
        });
    },
    toBuyHandler(p){
      // 跳转到订单确认页面，并且携带数据p
      this.$router.push({
        path:"/manager/order_confirm",
        query:p
      })
    },
    // 加载栏目信息
    loadCategories(){
      let url = "/category/findAll";
      get(url).then((response)=>{
        // 将查询结果，数组中的前6个元素获取到
        this.categories = response.data.slice(0,6);
      })
    },
    // 加载产品信息
    loadProducts(){
      let url = "/product/query"
      let params = { page:0, pageSize:100 }
      post(url,params).then((response)=>{
        this.products = response.data.list;
      })
    }
  }
}
</script>
<style scoped>
.box {
    width: 400px;
    height: 300px;
    /* border: 20px solid; */
}
.home {
  padding-bottom: 50px;
}
.header {
  height: 300px;
  overflow: hidden;
}
.header img {
  width: 100%;
}
</style>