<template>
  <div class="about">
    <h1>关于页面</h1>
    <input v-model.number="number" type="number" step="20">
    <p>{{ animatedNumber }}</p>
  </div>
</template>
<script>
import {TweenLite} from 'gsap'     // yarn add gsap
export default {
  data() {
    return{
      number: 0,
      tweenedNumber: 0
    }
  },
  computed: {
    animatedNumber: function() {
      return this.tweenedNumber.toFixed(0);
    }
  },
  watch: {
    number: function(newValue) {
      TweenLite.to(this.$data, 0.5, { tweenedNumber: newValue });
    }
  }
}
</script>

<style>
  .about{
    text-align: center;
  }
  .test{
    height: 200px; width: 200px; background: red; color: white;
  }
</style>
