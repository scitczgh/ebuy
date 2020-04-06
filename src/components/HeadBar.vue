<template>
  <div class="headBar">
    <van-sticky>
        <van-nav-bar
            title="川信e站"
            left-text="返回"
            right-text="按钮"
            left-arrow
            @click-left="onClickLeft"
            @click-right="onClickRight"
        >
            <template #right><van-icon name="scan" size="1.5rem"/></template>
        </van-nav-bar>
    </van-sticky>
  </div>
</template>

<script>
export default {
    methods: {
        onClickLeft() {
            this.$router.go(-1)
        },
        onClickRight() {
            this.$router.go(1)
        }
    }
}
</script>

<style>

</style>