<template>
  <div>
    <div class="images">
      <div v-for="(image, index) in images" :class="`image-${index + 2}`" :key="index"></div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        imageCount: 7
      }
    },
    computed: {
      images() {
        return new Array(this.imageCount - 1).fill(true)
      }
    }
  }
</script>

<style lang="less" scoped>
  .images {
    font-size: 0;
    & > div {
      width: 50vw;
      height: 50vw;
      display: inline-block;
      margin: 0;
    }

    .images(@n, @i: 1) when (@i =< @n) {
      .image-@{i} {
        background: url('../assets/photo/@{i}.jpg') no-repeat center center;
        background-size: cover;
      }
      .images(@n, (@i + 1));
    }

    .images(7)

  }
</style>
