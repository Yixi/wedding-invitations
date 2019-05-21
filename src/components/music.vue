<template>
  <div class="audio">
    <audio src="http://prutdia4z.bkt.clouddn.com/m.mp3" ref="audio"></audio>
  </div>
</template>

<script>
  export default {
    mounted() {
      this.$nextTick(() => {
        this.$refs.audio.play()
      })
    }
  }
</script>

<style lang="less" scoped>
  .audio {
    position: fixed;
    width: 100%;
    bottom: 0;
    left: 0;
  }

</style>
