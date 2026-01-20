<template>
  <!-- 游戏开始时显示的界面 -->
  <div class="start-screen">
    <h1>Doodle Jump</h1>
    <p>使用 ← → 键或 A D 键移动角色</p>
    <button @click="startGame">开始游戏</button>
  </div>
</template>

<script setup>
// 用于定义组件可以触发的事件
const emit = defineEmits(['start'])

// 点击开始按钮时
const startGame = () => {
  emit('start')
}
</script>

<style scoped>
.start-screen {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  
  background: rgba(255, 255, 255, 0.95);
  
  padding: 40px;
  border-radius: 20px;
  
  text-align: center;
  
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
  
  min-width: 300px;
}

/* 标题 */
h1 {
  color: #667eea;
  
  margin-bottom: 20px;
  
  font-size: 32px;
}

/* 说明 */
p {
  color: #333;
  
  margin-bottom: 25px;
  
  font-size: 18px;
}

/* 按钮 */
button {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  
  color: white;
  
  border: none;
  padding: 15px 40px;
  
  font-size: 18px;
  
  border-radius: 30px;
  
  cursor: pointer;
  
  transition: transform 0.2s, box-shadow 0.2s;
  
  font-weight: bold;
}

/* 鼠标悬停时的按钮 */
button:hover {
  transform: translateY(-2px);
  
  box-shadow: 0 5px 20px rgba(102, 126, 234, 0.4);
}

/* 鼠标按下时的按钮 */
button:active {
  transform: translateY(0);
}
</style>