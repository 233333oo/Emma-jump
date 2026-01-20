<template>
  <!-- 玩家角色组件 -->
  <!-- 使用 img 元素显示玩家角色图片 -->
  <img 
    :src="playerImage" 
    class="player" 
    :style="playerStyle"
    alt="玩家角色"
  />
</template>

<script setup>
// 导入 Vue 的计算属性函数
import { computed } from 'vue'

const props = defineProps({
  x: {
    type: Number,      // 玩家的 x 坐标
    required: true   
  },  
  y: {
    type: Number,      // 玩家的 y 坐标
    required: true     
  },
  width: {
    type: Number,      // 玩家宽度
    default: 50        // 默认50 像素
  },
  height: {
    type: Number,      // 玩家高度
    default: 50        // 默认50 像素
  },
  direction: {
    type: Number,      // 角色朝向（1 表示向右，-1 表示向左）
    default: 1         // 默认向右
  },
  velocityY: {
    type: Number,      // 垂直速度
    default: 0
  },
  scale: {
    type: Number,      // 角色缩放比例
    default: 1         // 默认为1（不缩放）
  }
})

// 根据垂直速度判断是否在跳跃，选择对应的图片
const playerImage = computed(() => {
  // 如果垂直速度小于 0（向上），显示跳跃姿态
  if (props.velocityY < 0) {
    return '/艾玛  跳  .png'
  }
  // 否则显示站立姿态
  return '/艾玛.png'
})

const playerStyle = computed(() => ({
  // 水平位置
  left: `${props.x}px`,
  // 垂直位置
  top: `${props.y}px`,
  // 宽度
  width: `${props.width}px`,
  // 高度
  height: `${props.height}px`,
  //  transform 实现角色翻转和缩放
  // scaleX(1) 表示正常显示，scaleX(-1) 表示水平翻转
  // scale() 控制整体缩放
  transform: `scaleX(${props.direction}) scale(${props.scale})`
}))
</script>

<style scoped>
/* 玩家角色的主样式 */
.player {
  /* 通过 left 和 top 属性控制位置 */
  position: absolute;
  
  /* 图片自适应填充 */
  object-fit: contain;
  
  /* 添加阴影，增加立体感 */
  filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.2));
}
</style>