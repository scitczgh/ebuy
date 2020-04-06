<template>
  <div class="car box">
    <h3>二手易物</h3>
    <van-checkbox v-model="isCKAll" shape="square" @change='ckAll'>二手物品列表</van-checkbox>
    <hr>
    <van-cell-group>
      <van-cell v-for="(g,index) in goods" :key='index'>
        <template #title>
            <van-row type="flex" justify="space-between" align='center'>
                <van-col span="3">
                    <van-checkbox v-model="g.isCK"></van-checkbox>
                </van-col>
                <van-col span="5">
                    <van-image width="40" height="50" :src='g.pic'/>
                </van-col>
                <van-col span="9">
                    <div style='color:#333;font-size:11px;'>{{g.name}}</div>
                    <span style='color:#f00;font-size:10px;'>￥{{g.price}}</span>
                </van-col>
                <van-col span="7" style='text-align:right'>
                    <van-stepper v-model="g.num" input-width="26px" button-size="22px"/>
                </van-col>
            </van-row>
        </template>
      </van-cell>
    </van-cell-group>
    <h3>总计：{{anTotal}}</h3>
  </div>
</template>

<script>
import {TweenLite} from 'gsap'     // yarn add gsap
export default {
  data() {
    return {
      goods: [
        { name: "充电线", pic: require('../assets/img/sjx.png'), price: 15, num: 2, isCK: true },
        { name: "手机壳", pic: require('../assets/img/sjk.png'), price: 25, num: 1, isCK: true },
        { name: "华为P40 Pro", pic: require('../assets/img/sj.png'), price: 4200, num: 1, isCK: true }
      ],
      isCKAll: true,
      twTotal: 0
    };
  },
  methods: {
    setNum(fh, i) {
      if (fh == "-") {
        if (this.goods[i].num > 1) --this.goods[i].num;
      } else {
        ++this.goods[i].num;
      }
    },
    ckAll() {
      for (let g of this.goods) {
        g.isCK = this.isCKAll;
      }
    }
  },
  computed: {
    total: function() {
      let sum = 0;
      for (let g of this.goods) {
        if (g.isCK) sum += g.num * g.price;
      }
      TweenLite.to(this.$data, 0.5, { twTotal: sum });
      return sum;
    },
    anTotal: function() {
      return this.twTotal.toFixed(0);
    }
  },
  watch: {
    total: function(newValue) {
        TweenLite.to(this.$data, 0.5, { twTotal: newValue });
    }
  }
};
</script>

<style>
</style>