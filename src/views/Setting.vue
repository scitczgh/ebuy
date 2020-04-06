<template>
    <div class="setting">
        <h3>设置</h3>
        <van-field
            v-model="username"
            name="姓名"
            label="姓名"
            placeholder="请输入姓名"
            :rules="[{ required: true, message: '请输入姓名' }]"
        />
        <van-cell title="新消息提醒" icon="volume-o">
            <van-switch v-model="checked" slot="right-icon" size="24px"/>
        </van-cell>
        <van-cell title='帮助' isLink icon="question-o"></van-cell>
        <van-cell title='关于' isLink icon="apps-o" value='V1.0'></van-cell>
    </div>
</template>
<script>
export default {
    data(){
        return {
            username:'',
            checked: true
        }
    }
}
</script>
<style lang="less" scoped>
    .setting {
        h3 { text-indent: 20px; }
    }
</style>