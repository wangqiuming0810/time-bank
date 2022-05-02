<template>
<!--  轮播图-->
  <div class="slide">
    <el-carousel  >
      <el-carousel-item v-for="item in images" :key="item">
        <img :src="item" >
      </el-carousel-item>
    </el-carousel>
  </div>
</template>

<script>
export default {
  name: "SlideView",
  data(){
    return {
      images:[
        // "https://www.nstimebank.com/timebank/thumb/upload/imageTab/1645579276257.png?w=666&h=280",
        "https://www.nstimebank.com/timebank/thumb/upload/imageTab/1641886595398.png?w=666&h=280",
        "https://www.nstimebank.com/timebank/thumb/upload/imageTab/1641886421787.png?w=666&h=280",
        "https://www.nstimebank.com/timebank/thumb/upload/imageTab/1625105282024.png?w=666&h=280"
      ]
    }
  }
}
</script>

<style scoped>
  .slide{
    width: 666px;
    height: 288px;
    /*border: 1px solid gray;*/
  }
</style>
