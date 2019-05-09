<template>
  <div class="slider">
    <div class="images">
      <transition name="fade" mode="in-out">
        <div :class="currentImageClass" :key="currentImageClass"></div>
      </transition>
    </div>
    <div class="overlay">

      <div class="qinjian">
        <div><img src="./../assets/hunli.png" alt=""></div>
        <div><img src="./../assets/qingjian.png" alt=""></div>
      </div>

      <div class="info">
        刘应皓 & 叶子
      </div>
      <div class="wording">
        诚邀您参加我们的婚礼
      </div>
      <div class="date">
        2019/07/07
      </div>
      <div class="address">
        天之府温德姆至尊豪庭大酒店
      </div>
      <div class="countdown">
        <countdown end="July 7, 2019"></countdown>
      </div>
      <div class="border"></div>
    </div>

  </div>
</template>

<script>

  import Countdown from 'vuejs-countdown'

  const PIC_SWITCH_TIME = 10 * 1000

  export default {
    components: {
      Countdown
    },
    name: 'HelloWorld',
    props: {
      msg: String
    },
    data() {
      return {
        currentImageIndex: 1,
        imageCount: 7
      }
    },
    mounted() {
      this.initSlider()
    },
    computed: {
      currentImageClass() {
        return `image-${this.currentImageIndex}`
      }
    },
    methods: {
      initSlider() {
        setTimeout(this.switchSlider, PIC_SWITCH_TIME)
      },

      switchSlider() {
        if (this.currentImageIndex < this.imageCount) {
          this.currentImageIndex++;
        } else {
          this.currentImageIndex = 1;
        }
        setTimeout(this.switchSlider, PIC_SWITCH_TIME)
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">


  .slider {
    position: relative;
  }

  .images {
    position: relative;
    z-index: 1;
    height: 100vh;

    & > div {
      width: 100%;
      height: 100vh;
      position: absolute;
      top: 0;
      left: 0;
    }

    .images(@n, @i: 1) when (@i =< @n) {
      .image-@{i} {
        background: url('../assets/photo/@{i}.jpg') no-repeat center center;
        background-size: cover;
      }
      .images(@n, (@i + 1));
    }

    .images(7);

  }

  .overlay {
    background: rgba(0, 0, 0, 0.45) url(data:image/svg+xml;base64,PHN2ZyB2ZXJzaW9uPSIxLjEiIGlkPSJMYXllcl8xIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4PSIwcHgiIHk9IjBweCINCgkgd2lkdGg9IjIwcHgiIGhlaWdodD0iMjBweCIgdmlld0JveD0iMCAwIDIwIDIwIiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCAyMCAyMDsiIHhtbDpzcGFjZT0icHJlc2VydmUiPg0KPHBhdHRlcm4gIHdpZHRoPSIyIiBoZWlnaHQ9IjIiIHBhdHRlcm5Vbml0cz0idXNlclNwYWNlT25Vc2UiIGlkPSJOZXdfUGF0dGVybl80IiB2aWV3Qm94PSIwIC0yIDIgMiIgc3R5bGU9Im92ZXJmbG93OnZpc2libGU7Ij4NCgk8Zz4NCgkJPHBvbHlnb24gc3R5bGU9ImZpbGw6bm9uZTsiIHBvaW50cz0iMCwtMiAyLC0yIDIsMCAwLDAgCQkiLz4NCgkJDQoJCQk8bGluZWFyR3JhZGllbnQgaWQ9IlNWR0lEXzFfIiBncmFkaWVudFVuaXRzPSJ1c2VyU3BhY2VPblVzZSIgeDE9IjAuNSIgeTE9Ii0xNjM2MSIgeDI9IjEuNSIgeTI9Ii0xNjM2MSIgZ3JhZGllbnRUcmFuc2Zvcm09Im1hdHJpeCgxIDAgMCAtMSAwIC0xNjM2MikiPg0KCQkJPHN0b3AgIG9mZnNldD0iMCIgc3R5bGU9InN0b3AtY29sb3I6IzAwMDAwMCIvPg0KCQkJPHN0b3AgIG9mZnNldD0iMSIgc3R5bGU9InN0b3AtY29sb3I6IzAwMDAwMDtzdG9wLW9wYWNpdHk6MCIvPg0KCQk8L2xpbmVhckdyYWRpZW50Pg0KCQk8cG9seWdvbiBzdHlsZT0iZmlsbDp1cmwoI1NWR0lEXzFfKTsiIHBvaW50cz0iMS41LC0wLjUgMC41LC0wLjUgMC41LC0xLjUgMS41LC0xLjUgCQkiLz4NCgk8L2c+DQo8L3BhdHRlcm4+DQo8cmVjdCBzdHlsZT0ib3BhY2l0eTowLjY7ZmlsbDp1cmwoI05ld19QYXR0ZXJuXzQpOyIgd2lkdGg9IjIwIiBoZWlnaHQ9IjIwIi8+DQo8L3N2Zz4=);
    height: 100%;
    left: 0;
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    z-index: 2;
    text-align: center;
    color: fade(#fff, 85%);

    @padding: 15px;
    @w: 100px;
    @h: 150px;

    &:before {
      content: ' ';
      width: @w;
      height: @h;
      position: absolute;
      left: @padding;
      top: @padding;
      border-top: 1px solid #fff;
      border-left: 1px solid #fff;
    }

    &:after {
      content: ' ';
      width: @w;
      height: @h;
      position: absolute;
      right: @padding;
      bottom: @padding;
      border-right: 1px solid #fff;
      border-bottom: 1px solid #fff;
    }
  }

  .info {
    color: white;
    font-size: 2em;
    margin-top: 5vh;
  }

  .qinjian {
    margin-top: 17vh;
    width: 140px;
    height: 130px;
    padding-top: 10px;
    display: inline-block;
    background: rgba(0,0,0,.2);
  }

  .date {
    margin-top: 3vh;
    font-size: 23px;
    letter-spacing: 2px;
  }

  .address {
    font-size: 12px;
  }

  .wording {
    margin-top: 3vh;
  }

  .countdown {
    /*position: absolute;*/
    /*width: 100%;*/
    /*text-align: center;*/
    /*bottom: 2vh;*/
    margin-top: 1vh;
    transform: scale(0.6);

  }



  .fade-enter-active, .fade-leave-active {
    transition: opacity 2s ease-in-out;
  }

  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
</style>
