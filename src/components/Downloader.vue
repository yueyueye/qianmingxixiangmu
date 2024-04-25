<template>
  <div>
    <!-- Canvas元素用于绘制电子签名 -->
    <canvas
      ref="canvas"
      :width="canvasWidth"
      :height="canvasHeight"
      @mousedown="startDrawing"
      @mousemove="draw"
      @mouseup="finishDrawing"
    ></canvas>
    <!-- 清除按钮，点击后清除Canvas上的内容 -->
    <button @click="clearCanvas">Clear</button>
    <!-- 保存按钮，点击后保存签名数据 -->
    <button @click="saveSignature">Save</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      canvasWidth: 400,
      canvasHeight: 200,
      drawing: false,
      signatureData: null
    };
  },
  methods: {
    // 开始绘制签名
    startDrawing(event) {
      this.drawing = true;
      const canvas = this.$refs.canvas;
      this.ctx = canvas.getContext('2d');
      this.ctx.beginPath();
      const x = event.offsetX;
      const y = event.offsetY;
      this.ctx.moveTo(x, y);
    },
    // 绘制签名
    draw(event) {
      if (this.drawing) {
        const x = event.offsetX;
        const y = event.offsetY;
        this.ctx.lineTo(x, y);
        this.ctx.stroke();
      }
    },
    // 完成绘制签名
    finishDrawing() {
      this.drawing = false;
    },
    // 清除Canvas上的内容
    clearCanvas() {
      const canvas = this.$refs.canvas;
      this.ctx.clearRect(0, 0, canvas.width, canvas.height);
    },
    // 保存签名数据
    saveSignature() {
      this.signatureData = this.$refs.canvas.toDataURL();
      console.log( this.signatureData);
    }
  }
};
</script>

<style>
canvas {
  border: 1px solid #000;
}
</style>
