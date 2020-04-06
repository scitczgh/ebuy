<template>
  <div class="home">
    <van-swipe class="my-swipe" :autoplay="3000" indicator-color="white" id="logo">
      <van-swipe-item v-for="(image, index) in images" :key="index">
        <img v-lazy="image" />
      </van-swipe-item>
    </van-swipe>
    <div class="box">
      <van-button @click="show()">显示</van-button>
      <van-button @click="hide()">隐藏</van-button>
    
      <hr>
      
      <van-button @click="isDing=true">显示</van-button>
      <van-button @click="isDing=false">隐藏</van-button>

      <transition name="mycss"> 
        <p v-show="isDing">迈着猫步慢慢走</p>
      </transition>
      
      <!-- <transition name="ding">-->
      <transition name="van-slide-left"
        @before-enter="beforeEnter" 
        @enter="enter" 
        @after-enter="afterEnter"
        @before-leave="beforeLeave" 
        @leave="leave" 
        @after-leave="afterLeave"
      >
        <div v-show="isDing">
            测试元素<br>
            我可以有过渡效果吗2 
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import { TweenLite } from 'gsap'     // yarn add gsap
import { Lazyload } from 'vant';
Vue.use(Lazyload);

export default {
  name: 'Home',
   data() {
    return {
      isDing: true,
      images: [
        require('../assets/img/sw03.jpg'),
        require('../assets/img/sw02.jpg'),
        require('../assets/img/sw01.jpg'),
      ]
    }
  },
  methods:{
    show () {     // 显示
        TweenLite.to('#logo', 0.8, {
            opacity: 1,
            onComplete () {
          }
        })
    },
    hide () {     // 隐藏
        TweenLite.to('#logo', 0.8, {
            opacity: 0,
            onComplete () {
          }
        })
    },
    beforeEnter() {
      console.log('动画进入之前');
    },
    enter() {
      console.log('动画进入');
    },
    afterEnter(el) {
      console.log('动画进入之后');
      el.style.color = '#333';
    },
    beforeLeave() {
      console.log('动画即将之前');
    },
    leave() {
      console.log('动画离开');
    },
    afterLeave(el) {
      console.log('动画离开之后');
      el.style.color = '#f00';
    }
  }
}
</script>

<style lang='less'>
  .home {text-align: center;}
  .my-swipe  .van-swipe-item {
    text-align: center;
    img {
      width:100%;
      height:160px;
    }
  }
  .ding-enter-active, .ding-leave-active {
    transition: opacity .5s;
  }
  .ding-enter, .ding-leave-to{
    opacity: 0;
  }
  
  p { width: 300px; height: 30px;}

  .mycss-enter-active, .mycss-leave-active { transition: all 3s ease;  }

  .mycss-enter-active { opacity: 1;  width: 300px; }

  .mycss-leave-active { opacity: 0;  width: 100px;}

  /* .fade-enter需要放在.fade-enter-active的后面 */
  .mycss-enter {  opacity: 0;  width: 100px; }
</style>