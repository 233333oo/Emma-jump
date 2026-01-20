<template>
  <!-- 道具组件 -->
  <div class="item" :class="`item-${type}`" :style="itemStyle">
    <!-- 火箭图标 -->
    <span v-if="type === 'rocket'" class="icon">🚀</span>
    <!-- 保护帽图标 -->
    <span v-else-if="type === 'shield'" class="icon">🛡️</span>
    <!-- 分数加成图标 -->
    <span v-else-if="type === 'bonus'" class="icon">⭐</span>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  x: {
    type: Number,
    required: true
  },
  y: {
    type: Number,
    required: true
  },
  size: {
    type: Number,
    default: 30
  },
  type: {
    type: String,
    required: true
  }
})

const itemStyle = computed(() => ({
  left: `${props.x}px`,
  top: `${props.y}px`,
  width: `${props.size}px`,
  height: `${props.size}px`
}))
</script>

<style scoped>
.item {
  position: absolute;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
  animation: float 2s ease-in-out infinite;
}

.item-rocket {
  background: linear-gradient(135deg, #4ECDC4, #44A08D);
}

.item-shield {
  background: linear-gradient(135deg, #A8E6CF, #88D8B0);
}

.item-bonus {
  background: linear-gradient(135deg, #FFE66D, #F7D794);
}

.icon {
  font-size: 18px;
  filter: drop-shadow(0 1px 2px rgba(0, 0, 0, 0.2));
}

.icon-image {
  width: 100%;
  height: 100%;
  object-fit: contain;
  filter: drop-shadow(0 1px 2px rgba(0, 0, 0, 0.2));
}

@keyframes float {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-5px);
  }
}
</style>