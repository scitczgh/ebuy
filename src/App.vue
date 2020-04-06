<template>
  <div id="scitc-app">
    <HeadBar />
    <!-- transition name="van-slide-left" mode='out-in' -->
    <transition name='fade' mode="out-in">
      <router-view/>
    </transition>
    <FootBar />
  </div>
</template>

<script>
import HeadBar from './components/HeadBar'
import FootBar from './components/FootBar'
export default {
  components:{ HeadBar, FootBar }
}
</script>

<style>
  .fade-enter-active {
    transition: transform .6s;
  }
  .fade-enter, .fade-leave-to{
    transform: translateX(-100%);
  }
</style>
