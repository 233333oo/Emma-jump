// 游戏画布组件

<template>
  
  
  <canvas ref="canvasRef" :width="width" :height="height"></canvas>
</template>

<script setup>
// 导入 Vue 的生命周期函数
import { ref, onMounted, onUnmounted } from 'vue'

//组件属性

const props = defineProps({
  width: {
    type: Number,
    default: 400,   
  },
  height: {
    type: Number,  
    default: 600,
  }
})

//组件可以触发的事件
const emit = defineEmits(['canvas-ready'])


//用于创建响应式变量，当变量变化时，界面会自动更新
const canvasRef = ref(null)  // 存储 canvas 元素的引用

// 生命周期钩子
// 挂载到页面后执行
onMounted(() => {
  // 将 canvas 元素传递给父组件
  emit('canvas-ready', canvasRef.value)
})


// defineExpose 用于定义哪些内容可以被父组件访问
defineExpose({
  canvasRef  
})
</script>

//样式
<style scoped>
canvas {
  border-radius: 10px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
  background: url('/画布.png') no-repeat center center;
  background-size: cover;
}
</style>