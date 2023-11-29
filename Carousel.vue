<template>
  <div class="carousel">
    <div class="slider" :style="{ transform: 'translateX(' + translateValue + 'px)' }">
      <div v-for="(item, index) in items" :key="index" class="slide" :style="{ backgroundColor: item.color }">
        <!-- 内容或图片放在这里 -->
      </div>
    </div>
    <button @click="prevSlide" class="prev">Previous</button>
    <button @click="nextSlide" class="next">Next</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0,
      translateValue: 0,
      items: [
        { color: 'red' },
        { color: 'green' },
        { color: 'blue' },
        { color: 'orange' },
        { color: 'grey' },
        { color: 'purple' },
        // 添加更多项目
      ],
    };
  },
  methods: {
    prevSlide() {
      if (this.currentIndex > 0) {
        this.currentIndex--;
        this.updateTranslateValue();
      }
    },
    nextSlide() {
        if (this.currentIndex < this.items.length - 3) {
            this.currentIndex++;
        } else {
            this.currentIndex = 0;
        }
        this.updateTranslateValue();
    },
    updateTranslateValue() {
      this.translateValue = -this.currentIndex * 400; // 400是每个方块的宽度
    },
  },
};
</script>

<style scoped>
.carousel {
  position: relative;
  overflow: hidden;
  width: 100%;
}

.slider {
  display: flex;
  transition: transform 0.5s ease;
}

.slide {
  width: 400px;
  height: 400px;
  flex-shrink: 0;
}

.prev,
.next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  cursor: pointer;
}

.prev {
  left: 10px;
}

.next {
  right: 10px;
}
</style>