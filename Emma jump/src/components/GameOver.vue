<template>
  <!-- 游戏结束界面组件 -->
 
  <div class="game-over">
    <h2>游戏结束</h2>
    <p>你的分数: {{ score }}</p>
    <button @click="restartGame">重新开始</button>
  </div>
</template>

<script setup>

const props = defineProps({
  score: {
    type: Number,      // 最终分数
    required: true     // 必须提供的属性
  }
})


// 定义组件可以触发的事件
const emit = defineEmits(['restart'])


// 点击重新开始按钮时调用此函数
const restartGame = () => {
  // 触发 'restart' 事件，通知父组件重新开始游戏
  emit('restart')
}
</script>

<!--  组件样式  -->
<style scoped>
/* 游戏结束界面容器 */
.game-over {
  /* 绝对定位，居中显示 */
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  
  /* 背景颜色：半透明白色 */
  background: rgba(255, 255, 255, 0.95);
  
  /* 内边距 */
  padding: 40px;
  
  /* 圆角边框 */
  border-radius: 20px;
  
  /* 文字居中 */
  text-align: center;
  
  /* 添加阴影，增加立体感 */
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
  
  /* 最小宽度 */
  min-width: 300px;
}

/* 标题样式 */
h2 {
  /* 文字颜色：紫色渐变 */
  color: #667eea;
  
  /* 下边距 */
  margin-bottom: 20px;
  
  /* 字体大小 */
  font-size: 32px;
}

/* 分数显示样式 */
p {
  /* 文字颜色：深灰色 */
  color: #333;
  
  /* 下边距 */
  margin-bottom: 25px;
  
  /* 字体大小 */
  font-size: 18px;
}

/* 按钮样式 */
button {
  /* 渐变背景色：从紫色到深紫色 */
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  
  /* 文字颜色：白色 */
  color: white;
  
  /* 去掉边框 */
  border: none;
  
  /* 内边距 */
  padding: 15px 40px;
  
  /* 字体大小 */
  font-size: 18px;
  
  /* 圆角边框 */
  border-radius: 30px;
  
  /* 鼠标指针：手型 */
  cursor: pointer;
  
  /* 过渡动画效果 */
  transition: transform 0.2s, box-shadow 0.2s;
  
  /* 字体粗细 */
  font-weight: bold;
}

/* 鼠标悬停时的按钮样式 */
button:hover {
  /* 向上移动 2 像素 */
  transform: translateY(-2px);
  
  /* 增加阴影 */
  box-shadow: 0 5px 20px rgba(102, 126, 234, 0.4);
}

/* 鼠标按下时的按钮样式 */
button:active {
  /* 恢复原位 */
  transform: translateY(0);
}
</style>