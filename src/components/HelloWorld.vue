<template>
  <div class="hello">
    <div class="header">
      <span>
        Λd astra
      </span>
    </div>
    <carousel class="VueCarousel-slide">
      <slide v-for="img in imgs" :key="img"
        class="slide">
        <img :src="img">
      </slide>
    </carousel>
    <div class="info">
      <img src='../assets/logo.png'>
      <a href="https://www.instagram.com/ad_astra_adas/?r=nametag">
        <img src='../assets/insta.png'>
        Instagram
      </a>
      <span @click="open()">・ 詳細情報</span>
      <div :class="isAnime ? 'open animation' : 'aaa'">
        <i></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
    'carousel': VueCarousel.Carousel,
    'slide': VueCarousel.Slide
  },
  data() {
    return {
      // 開閉
      isOpen: false,
      // アニメーション開始
      isAnime: false,
      // 画像のリスト
      imgs: [ 
        require('../assets/gazou1.png'),
        require('../assets/sake.png'),
        require('../assets/tabemono.png'),
        require('../assets/ikemen.png'),
        require('../assets/sake.png'),
        require('../assets/kame.png'),
      ],
    };
  },
  methods: {
    // 亀の開閉
    open() {
      this.isAnime = !this.isAnime;
    },
  },
}
</script>


<style lang="scss" scoped>
.hello{
  width: 100vh;
  height: 100%;
  display: flex;
  align-items: center;
  flex-direction: column;
  .header{
    width: 100%;
    min-height: 60px;
    background: #0000003b;
    box-shadow: 3px 3px 27px 10px rgba(0, 0, 0, 0.6) inset;
    display: flex;
    justify-content: center;
    align-items: flex-start;
    padding-top: 1em;
    span{
      display: flex;
      justify-content: center;
      align-items: flex-start;
      color: #ebe8e3;
      font-size: 2em;
      font-family: 'Times New Roman', Times, serif;
    }
  }
  .info{
    width: 70%;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    flex-direction: column;
    margin-top: 30px;
    height: 100%;
    img{
      border-radius: 50%;
      width: 130px;
      height: 130px;
    }
    a{
      margin-top: 30px;
      font-size: 1.5em;
      color: #fff;
      text-decoration: none;
      display: flex;
      justify-content: center;
      align-items: center;
      img{
        width: 50px;
        height: 50px;
        border-radius: 5px;
      }
    }
    span{
      margin-top: 30px;
      font-size: 16px;
      color: #fff;
      cursor: pointer;
    }
    .aaa{
      display: none;
    }
    .open{
      margin-top: 30px;
      color: #fff;
      font-size: 20px;
      width: 100%;
      height: 100px;
      i{
        width: 100%;
        display: inline-block;
        height: 100%;
        text-align: center;
        background: url('../assets/kame.png') no-repeat;
        background-size: 100% 100%;
      }
    }
    .animation {
      animation: 1s ease 0s 1 normal none running animation;
    }
    @keyframes animation {
      0% {
        opacity: 0;
        display: none;
      }
      10% {
        opacity: 0.1;
      }
      20% {
        opacity: 0.2;
      }
      30% {
        opacity: 0.3;
      }
      40% {
        opacity: 0.4;
      }
      50% {
        opacity: 0.5;
      }
      60% {
        opacity: 0.6;
      }
      70% {
        opacity: 0.7;
      }
      80% {
        opacity: 0.8;
      }
      90% {
        opacity: 0.9;
      }
      100% {
        opacity: 1;
      }
    }
  }
}
.VueCarousel-slide {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  box-sizing: border-box;
  .slide{
    width: 100%;
    height: 100%;
    img{
      width: 100%;
    }
  }
}
</style>
