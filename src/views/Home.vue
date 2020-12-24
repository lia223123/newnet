<template>
  <div id="home">
    <nav-bar class="nav_bar">
      <div v-for="(item, index) in title"
           :key="index"
           :class="{activeText:index === currentId}"
           @click="goPages(index)">{{item}}</div>
    </nav-bar>
    <div  class="up"><span @click="Up(currentId)" v-show="_up_show">上滑</span></div>
    <div  class="down"><span @click="Down(currentId)" v-show="_down_show">下滑</span></div>
    <el-carousel height="97vh"
                 direction="vertical"
                 :autoplay="false"
                 trigger="click"
                 ref="carousel"
                 indicator-position="none"
                 :loop="false">
      <el-carousel-item>
        <div class="medium_one">碧琪信息科技</div>
      </el-carousel-item>
      <el-carousel-item>
        <h3 class="medium_two">2</h3>
      </el-carousel-item>
      <el-carousel-item>
        <h3 class="medium_three">3</h3>
      </el-carousel-item>
      <el-carousel-item>
        <h3 class="medium_four">4</h3>
      </el-carousel-item>
    </el-carousel>

  </div>
</template>

<script>
import NavBar from "./homeChild/NavBar";
export default {
  name: 'Home',
  components:{
    NavBar
  },
  data(){
    return {
      currentId:0,
      title:['首页', '服务', '关于我们', '联系我们'],
    }
  },
  computed:{
    _up_show(){
      if(this.currentId === 0){
        return false
      }
      else return true
    },
    _down_show(){
      if(this.currentId === this.title.length-1){
        return false
      }
      else return true
    }
  },
  methods:{
    Up(index){
      if(index === 0){
        return
      }
      this.currentId--
      this.$refs.carousel.prev()
      this.down_show = true
    },
    Down(index){
      if(index === this.title.length-1){
        return
      }
      this.currentId++
      this.$refs.carousel.next()
    },
    goPages(index){
      this.$refs.carousel.setActiveItem(index)
      this.currentId = index
    }
  },
}
</script>

<style scoped>
.el-carousel__item h3 {
  color: #475669;
  font-size: 14px;
  opacity: 0.75;
  line-height: 200px;
  margin: 0;
}

.el-carousel__item:nth-child(1) {
  background-image: url('../assets/back01.jpg');
  background-size: 100% 100%;
}

.el-carousel__item:nth-child(2) {
  background-color: #98e752;
}
.el-carousel__item:nth-child(3) {
  background-color: #e8ce45;
}
.el-carousel__item:nth-child(4) {
  background-color: #d3dce6;
}
.medium_one{
  font: 50px Extra large;
  font-family: 阿里巴巴普惠体;
  color: #174678;
  position: absolute;
  top: 100px;
  left: 130px;
}
body{
  padding: 0;
}
.nav_bar{
  position: absolute;
  top: 20vh;
  z-index: 9;
  left: 0;
}
.nav_bar div{
  margin-left: 8px;
  height: 60px;
  width: 40px;
  text-align: right;
  font-size: 0;
  font-family: 阿里巴巴普惠体;
  border-top: 2px solid #fff;
  cursor: pointer;
  color: white;
}
.activeText{
  font-size: 18px !important;
  width: 80px !important;
}

.up{
  position: absolute;
  z-index: 9;
  text-align: center;
  width: 96%;
  top: 10px;
  color: #ffffff;
}
.up span{
  cursor: pointer;
}
.down{
  position: absolute;
  z-index: 9;
  text-align: center;
  width: 96%;
  bottom: 14px;
  color: #ffffff;
}
.down span{
  cursor: pointer;
}
</style>
