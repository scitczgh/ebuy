<template>
  <div class="news">
    <van-cell-group>
        <!-- 
            class="van-ellipsis" 
            :title="n.title.length>16?n.title.substr(0,16)+'…':n.title"  
        -->
        <van-cell 
            v-for="(n,i) of news" :key='i'
            :title="n.title.length>16?n.title.substr(0,16)+'…':n.title"  
            :label="n.time" 
            icon='chat-o'
            is-link
            to='/newsinfo'
        >
        </van-cell>
    </van-cell-group>
  </div>
</template>

<script>
export default {
    data(){
        return {
            news:[
                { nid: '1', title: '关于2020年春季学期线上教学的安排1', time: '2020-02-12' },
                { nid: '2', title: 'Web前端开发课程作业', time: '2020-02-12' },
                { nid: '3', title: '四川信息职业技术学院软件技术专业', time: '2020-02-12' },
                { nid: '4', title: '中国软件杯技能大赛选拔赛通知', time: '2020-02-12' },
                { nid: '5', title: '关于2020年春季学期线上教学的安排5', time: '2020-02-12' },
                { nid: '6', title: '关于2020年春季学期线上教学的安教学的安教学的安排6', time: '2020-02-12' },
                { nid: '7', title: '关于2020年春季学期线上教学的安排7', time: '2020-02-12' },
                { nid: '8', title: '关于2020年春季学期线上教学的安排8', time: '2020-02-12' },
                { nid: '9', title: '关于2020年春季学期线上教学的安排9', time: '2020-02-12' },
            ]
        }
    }
}
</script>

<style>
    .news { text-align: left; }
</style>
