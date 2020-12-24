<template>
  <el-carousel height="100%" direction="vertical" :autoplay="false">
    <slot></slot>
  </el-carousel>
</template>

<script>
export default {
  name: "Carousel",
  props:{
    autoplay:{
      type:Boolean,
      default:false
    }
  }
}
</script>

<style scoped>

</style>