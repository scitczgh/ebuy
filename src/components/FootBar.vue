<template>
  <div class="footBar">
    <van-tabbar v-model="active">
        <van-tabbar-item icon="home-o" to='/'>首页</van-tabbar-item>
        <van-tabbar-item icon="comment-o" to='/news'>新闻</van-tabbar-item>
        <van-tabbar-item icon="shopping-cart-o" to='/car'>易物</van-tabbar-item>
        <van-tabbar-item icon="setting-o" to='/setting'>设置</van-tabbar-item>
    </van-tabbar>
  </div>
</template>

<script>
export default {
    data() {
        return {
            active: 0
        }
    }
}
</script>

<style>

</style>