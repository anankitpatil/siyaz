<template>
<div class="car-slider" ref="container">
  <div class="overlay" ref="overlay" :style="{width: this.position + '%'}">
    <div class="btn" draggable="true" @dragstart="dragStart" @drag="handleDrag" @dragend="dragEnd" />
    <div class="shadow"></div>
  </div>
</div>
</template>

<script>
export default {
  name: 'CarSlider',
  data() {
    return {
      position: 50,
      initX: 0,
      currentP: 0
    }
  },
  methods: {
    dragStart(e) {
      this.initX = e.clientX
    },
    handleDrag(e) {
      if (e.clientX != 0) {
        this.currentP = (e.clientX - this.initX) / 1280 * 100 + this.position
        this.$refs.overlay.style.width = this.currentP + '%'
      }
    },
    dragEnd() {
      this.position = this.currentP
      return false
    }
  },
  created() {

  }
}
</script>
