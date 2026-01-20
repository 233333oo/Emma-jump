<template>
  
  <div class="game-container">
    
    <!-- 分数板组件：显示当前分数和最高分 -->
    <!-- 使用 v-bind（:）传递数据 -->
    <ScoreBoard :score="score" :high-score="highScore" />
    
    <!-- 游戏区域容器 -->
    <div class="game-area">
      
      <!-- 游戏画布组件：提供游戏的背景和画布 -->
      <GameCanvas ref="gameCanvasRef" width="400" height="600" />
      
      <!-- 游戏元素容器 -->
      <!-- gameStarted 为 true 时渲染 -->
      <div v-if="gameStarted" class="game-elements">
        
        <!-- 玩家角色组件 -->
        <!-- 传递玩家的位置、尺寸、朝向和垂直速度 -->
        <Player 
          :x="player.x" 
          :y="player.y" 
          :width="player.width" 
          :height="player.height"
          :direction="player.direction"
          :velocity-y="player.velocityY"
          :scale="1.5"
        />
        
        <!-- 保护帽指示器 -->
        <div v-if="hasShield" class="shield-indicator">🛡️</div>
        
        <!-- 道具组件列表 -->
        <Item
          v-for="(item, index) in items"
          :key="index"
          :x="item.x"
          :y="item.y"
          :size="item.size"
          :type="item.type"
        />
        
        <!-- 平台组件列表 -->
        <!-- 使用 v-for 循环渲染所有平台 -->
        <!-- :key 是必须的，帮助 Vue 高效更新列表 -->
        <Platform
          v-for="(platform, index) in platforms"
          :key="index"
          :x="platform.x"
          :y="platform.y"
          :width="platform.width"
          :height="platform.height"
          :color="platform.color"
        />
        
      </div>
      
      <!-- 游戏结束界面-->
      <!-- @restart 监听，调用 restartGame 函数 -->
      <GameOver v-if="gameOver" :score="score" @restart="restartGame" />
      
      <!-- 开始界面-->
      <!-- @start 监听，调用 startGame 函数 -->
      <StartScreen v-if="!gameStarted" @start="startGame" />
      
    </div>
  </div>
</template>


<script setup>
// 导入 Vue 的生命周期函数
import { onMounted, onUnmounted } from 'vue'

// 导入所有游戏组件
import ScoreBoard from './components/ScoreBoard.vue'
import GameCanvas from './components/GameCanvas.vue'
import Player from './components/Player.vue'
import Platform from './components/Platform.vue'
import Item from './components/Item.vue'
import GameOver from './components/GameOver.vue'
import StartScreen from './components/StartScreen.vue'

// 导入游戏逻辑函数
import { useGameLogic } from './composables/useGameLogic'

// 游戏逻辑
// 调用 useGameLogic 函数，解构出所有需要的状态和函数
const {
  score,           // 当前分数
  highScore,       // 最高分
  gameOver,        // 游戏是否结束
  gameStarted,     // 游戏是否已开始
  player,          // 玩家对象
  platforms,       // 平台数组
  items,           // 道具数组
  hasShield,       // 是否有保护帽
  startGame,       // 开始游戏函数
  restartGame,     // 重新开始游戏函数
  handleKeyDown,   // 键盘按下处理函数
  handleKeyUp      // 键盘松开处理函数
} = useGameLogic()

// 生命周期钩子 
// onMounted：组件挂载到页面后执行
onMounted(() => {
  // 添加键盘事件监听器
  
  window.addEventListener('keydown', handleKeyDown)
  
  window.addEventListener('keyup', handleKeyUp)
})

// 卸载前执行
onUnmounted(() => {
  // 移除键盘事件监听器
  // 防止内存泄漏，避免事件监听器重复添加
  window.removeEventListener('keydown', handleKeyDown)
  window.removeEventListener('keyup', handleKeyUp)
})
</script>

<!--样式-->
<style scoped>



.game-container {
  
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

/* 游戏区域容器 */
.game-area {
  position: relative;
  width: 400px;
  height: 600px;
  overflow: hidden;
}

/* 游戏元素容器 */
.game-elements {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

/* 保护帽指示器 */
.shield-indicator {
  position: absolute;
  top: 10px;
  right: 10px;
  font-size: 24px;
  animation: pulse 1s ease-in-out infinite;
  z-index: 100;
}

@keyframes pulse {
  0%, 100% {
    opacity: 1;
    transform: scale(1);
  }
  50% {
    opacity: 0.7;
    transform: scale(1.1);
  }
}
</style>