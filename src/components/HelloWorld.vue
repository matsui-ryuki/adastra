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
      <div class="btn-area">
        <span class="btn" @click="open('info')">詳細情報</span>
        <span class="btn" @click="open('pastEvent')">過去のイベント</span>
        <span class="btn" @click="open('nextEvent')">ボタン2</span>
      </div>
      <div :class="isAnime ? 'open animation' : 'aaa'">
        <div class="info-page" v-show="isSelectBtn === 'info'">
          <span>アドアステラとは...</span>
          <div class="close-icon close-btn-position" @click="closeInfo()"><span></span></div>
          <p>{{ astraText1 }}</p>
          <p>{{ astraText2 }}</p>
          <p>{{ astraText3 }}</p>
          <p>{{ astraText4 }}</p>
          <p class="caution">{{ astraText5 }}</p>
        </div>
        <div class="past-event-page" v-show="isSelectBtn === 'pastEvent'">
          <span>11月17日  BBQ🍖</span>
          <div class="close-icon close-btn-position" @click="closeInfo()"><span></span></div>
          <img class="event-img" src="../assets/BBQ1.png">
          <img class="event-img" src="../assets/BBQ2.png">
          <img class="event-img" src="../assets/BBQ3.png">
          <p>{{ astraText6 }}</p>
          <p>{{ astraText7 }}</p>
          <p>{{ astraText8 }}</p>
          <p>{{ astraText9 }}</p>
        </div>
        <div class="next-event-page" v-show="isSelectBtn === 'nextEvent'">
          <img src="../assets/kame.png">
          <div class="close-icon close-btn-position" @click="closeInfo()"><span></span></div>
        </div>
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
      // 押されたボタンによって開くものを変える
      isSelectBtn: null,
      // 画像のリスト
      imgs: [ 
        require('../assets/gazou1.png'),
        require('../assets/sake.png'),
        require('../assets/tabemono.png'),
        require('../assets/ikemen.png'),
        require('../assets/sake.png'),
        require('../assets/kame.png'),
      ],
      // アドアステラの詳細文
      astraText1:
        'アドアステラは2018年11月に発足した楽しみたい大学生、社会人向けのイベント団体となっております😁',
      astraText2:
        'コンセプトは「学生👨‍🎓」です。イベントに参加してくださる方や、初めて参加してくださる方も同じ学校に集まる仲間のような、誰もが楽しめるイベントを企画しております👨🏻‍💻',
      astraText3:
        'イベント内容としまして、BBQ🍖飲み会🍻花見🌸海🏖肝試し👻花火🎆など季節にあった、社会人になってからでは難しいような、側から見たら子どもみたいなそんな遊びを年齢、時間を忘れて楽しんでもらいたいと思っております。',
      astraText4:
        '初めての方、一人の方でも話しやすいような環境にしております‼️友達を誘っての参加、お一人様での参加どちらでも是非お待ちしております🤗',
      astraText5: 
        '⚠️当団体では、ご参加頂いた方を副業やセミナーなどに勧誘する行為は一切行っておりませんので、ご安心ください。もしいた場合はご報告よろしくお願いいたします。',
      astraText6: '初イベントのBBQの様子です‼️',
      astraText7:
        '「１１月で寒いやろ！」とかめちゃくちゃ幹事が責められていましたが、当日はかなり暖かく長袖一枚で過ごせるほど快適な気温でした🥺鶴見緑地公園のBBQ広場🐛で集まって開催しました😁',
      astraText8:
        'なんといって大きいお肉🍗が印象的です笑笑お酒もリキュールから作ったり、のんびり話しながら...zZZ',
      astraText9:
        'BBQの後は少しレクリエーションをして盛り上がってもらいました👨‍👩‍👧‍👧ここからアドアステラの始まりです🕺🏿',
    };
  },
  methods: {
    // ボタンごとの開閉
    open(type) {
      if (this.isSelectBtn === null) {
        this.isSelectBtn = type;
        this.isAnime = true;
      } else if (this.isSelectBtn !== type) {
        this.isSelectBtn = type;
        this.isAnime = true;
      } else if (this.isSelectBtn === type || this.isSelectBtn !== type) {
        this.isSelectBtn = null;
        this.isAnime = false;
      }
    },
    // 閉じる
    closeInfo() {
      this.isSelectBtn = null;
      this.isAnime = false;
    }
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
    .btn-area{
      width: 100%;
      .btn{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        margin-top: 20px;
        font-size: 16px;
        width: 100%;
        color: #fff;
        cursor: pointer;
      }
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
      display: flex;
      justify-content: center;
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
    .info-page, .past-event-page, .next-event-page{
      width: 95%;
      height: 400px;
      border-radius: 5px;
      background: #fff;
      font-size: 1em;
      display: flex;
      justify-content: center;
      text-align: center;
      flex-wrap: wrap;
      -webkit-overflow-scrolling: touch;
      overflow: hidden;
      overflow-y: auto;
      position: relative;
      span{
        color: #000;
        font-size: 1em;
      }
      p{
        margin: 10px 0px;
        font-size: 13px;
        color: #292929;
      }
      .caution{
        font-size: 15px;
        color: rgb(187, 190, 2);
      }
      .event-img{
        margin-top: 10px;
        border-radius: 0px;
        width: 70%;
        height: 35%;
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
// ばつボタン
.close-btn-position{
  position: absolute;
  top: 0rem;
  right: -1em;
}
.close-icon{
  display: inline-block;
  width: 40px;
  height: 40px;
  position: relative;
  cursor: pointer;
  span::before, span::after {
    display: block;
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 66%;
    height: 9%;
    margin: -8% 0 0 -42%;
    background: #000;
  }
  span::before {
    transform: rotate(-45deg);
  }
  span::after {
    transform: rotate(45deg);
  }
}
</style>
