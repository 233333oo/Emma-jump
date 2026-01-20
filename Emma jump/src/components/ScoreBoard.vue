<template>
  <!-- 显示当前分数和最高分 -->
  <div class="score-board">
    <div class="score">分数: {{ score }}</div>
    <div class="high-score">最高分: {{ highScore }}</div>
  </div>
</template>

<script setup>
const props = defineProps({
  score: {
    type: Number,      // 当前分数
    default: 0         // 默认值：0
  },
  highScore: {
    type: Number,      // 最高分
    default: 0         // 默认值：0
  }
})
</script>

<style scoped>
.score-board {
  display: flex;
  
  gap: 30px;           /* 两个分数之间的间距 */
  
  color: white;

  font-size: 20px;

  font-weight: bold;

  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}
</style>