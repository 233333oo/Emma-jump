<template>
<!-- 平台组件 -->
<!-- 使用 div 元素创建平台，通过 CSS 样式控制外观 -->
  <div class="platform" :style="platformStyle"></div>
</template>

<script setup>
// 导入 Vue 的计算属性函数
import { computed } from 'vue'

const props = defineProps({
  x: {
    type: Number,      // 平台的 x 坐标
    required: true    
  },
  y: {
    type: Number,      // 平台 y 坐标
    required: true     
  },
  width: {
    type: Number,      // 平台宽度
    default: 70        // 默认70 像素
  },
  height: {
    type: Number,      // 平台高度
    default: 15        // 默认15 像素
  },
  color: {
    type: String,      // 平台颜色
    default: '#4CAF50' // 默认绿色
  }
})

// computed 用于创建计算属性，会根据依赖的属性自动计算
// 当 props 中的值变化时，platformStyle 会自动重新计算
const platformStyle = computed(() => ({
  // 水平位置
  left: `${props.x}px`,
  // 垂直位置
  top: `${props.y}px`,
  // 宽度
  width: `${props.width}px`,
  // 高度
  height: `${props.height}px`,
  // 背景颜色
  backgroundColor: props.color
}))
</script>

<style scoped> 
/*平台的主样式 */
.platform {
  /* 通过 left 和 top 控制位置 */
  position: absolute;
  
  /* 圆角边框 */
  border-radius: 8px;
  
  /* 添加阴影 */
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

/* 创建平台的高光效果 */
.platform::after {
  content: ''; 
  
  /* 绝对定位 */
  position: absolute;
  
  /* 高光的位置 */
  top: 0;
  left: 0;
  right: 0;
  
  /* 高光的高度：平台高度的一半 */
  height: 50%;
  
  /* 高光颜色 */
  background: rgba(255, 255, 255, 0.3);
  
  /* 圆角边框 */
  border-radius: 8px 8px 0 0;
}
</style>