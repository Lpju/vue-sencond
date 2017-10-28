<template>
    <div>
        <!-- 1.利用mint-ui中的hear完成hear头部 -->
        <mt-header fixed title="hello world!"></mt-header>
        <!-- 2.路由站位 -->
        <router-view></router-view>
        <!-- 3.利用mui的barbutton完整底部 -->
        <nav class="mui-bar mui-bar-tab">
            <router-link class="mui-tab-item" to="/home">
                <span class="mui-icon mui-icon-home"></span>
                <span class="mui-tab-label">首页</span>
            </router-link>
            <router-link class="mui-tab-item" to="#tabbar-with-chat">
                <span class="mui-icon mui-icon-email"></span>
                <span class="mui-tab-label">消息</span>
            </router-link>
            <router-link class="mui-tab-item" to="/shopcar">
                <span class="mui-icon mui-icon-contact"><span class="mui-badge">0</span></span>
                <span class="mui-tab-label">购物车</span>
            </router-link>
            <router-link class="mui-tab-item" to="#tabbar-with-map">
                <span class="mui-icon mui-icon-gear"></span>
                <span class="mui-tab-label">设置</span>
            </router-link>
        </nav>
    </div>
</template>
<script>
    export default {
    data:function(){
        return {}
    },
    methods:{

    },
    created:function(){
     }
    }
</script>
<style scoped>
    /* scoped表示这个里面写的css代码只是在当前组件页面上有效，不会去影响到其 他组件页面 */

</style>