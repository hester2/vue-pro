<template>
  <div class="home-container">
    <mt-swipe class="binner-container" :auto="4000">
      <mt-swipe-item v-for="(item,index) in bannerList" :key="index">
        <a :href="item.url">
          <img :src="item.img">
        </a>
      </mt-swipe-item>
  </mt-swipe>
    <!-- 六宫格 -->
    <ul class="mui-table-view mui-grid-view mui-grid-9">
		            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                  <router-link to="/home/newsList">
		                    <img src="../../images/menu1.png" alt="">
		                    <div class="mui-media-body">新闻资讯</div> 
                        </router-link>
                        
                       
                        </li>
                       
		            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><router-link to="/home/photolist">
		                     <img src="../../images/menu2.png" alt="">
		                    <div class="mui-media-body">图片分享</div></router-link></li>
		            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><router-link to="/home/goodsList">
		                     <img src="../../images/menu3.png" alt="">
		                    <div class="mui-media-body">商品购买</div></router-link></li>
		            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		                     <img src="../../images/menu4.png" alt="">
		                    <div class="mui-media-body">留言反馈</div></a></li>
		            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		                     <img src="../../images/menu5.png" alt="">
		                    <div class="mui-media-body">视频专区</div></a></li>
		            <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
		                     <img src="../../images/menu6.png" alt="">
		                    <div class="mui-media-body">联系我们</div></a></li>
		        </ul>
  </div>
</template>

<script>
   import {Toast} from "mint-ui";

export default {
  data() {
       return {
         bannerList:[]
       };
     },
     created() {
       this.getBannerData();
     },
     methods:{
       getBannerData() {
         this.$http.get("http://www.lovegf.cn:8899/api/getlunbo").then(result => {
           if (result.body.status === 0) {
             this.bannerList = result.body.message;
           }else{
             Toast("获取轮播图数据失败!请重试");
           }
         });
       }
     }
   };
</script>
<style lang="less">
     .home-container{
       width: 100%;
       .binner-container{
         height: 300px;
         width: 100%;
         a img{
           height: 100%;
           width: 100%;
           display: block;
         }
       }
       .mui-grid-view{
         background-color: #fff;
         border:none;
         width: 100%;
           .mui-table-view-cell{
               border:none;
               width: 33.33%;
               font-size: 12px;
               img{
                 height: 60px;
                 width: 60px;

               }
           }
       }
     }
</style>

