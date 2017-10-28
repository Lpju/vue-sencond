<template>
    <div id="tmpl">
        <mt-swipe :auto="2000">
            <mt-swipe-item v-for="item in lunbo">
                <img :src="item.img">
            </mt-swipe-item>
        </mt-swipe>
        <div class="mui-content">
            <ul class="mui-table-view mui-grid-view mui-grid-9">
                <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                    <router-link to="/news/newslist">
                        <span class="mui-icon mui-icon-home"></span>

                        <div class="mui-media-body">新闻资讯</div>
                    </router-link>
                </li>
                <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                    <router-link to="/photo/photolist">
                        <span class="mui-icon mui-icon-email"></span>

                        <div class="mui-media-body">图片分享</div>
                    </router-link>
                </li>
                <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                    <router-link to="/goods/goodslist">
                        <span class="mui-icon mui-icon-chatbubble"></span>

                        <div class="mui-media-body">商品购买</div>
                    </router-link>
                </li>
                <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                    <router-link to="/feedback">
                        <span class="mui-icon mui-icon-location"></span>

                        <div class="mui-media-body">留言反馈</div>
                    </router-link>
                </li>
                <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                    <router-link to="/vide">
                        <span class="mui-icon mui-icon-search"></span>

                        <div class="mui-media-body">视屏专区</div>
                    </router-link>
                </li>
                <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
                    <router-link to="/callme">
                        <span class="mui-icon mui-icon-phone"></span>

                        <div class="mui-media-body">联系我们</div>
                    </router-link>
                </li>
            </ul>
        </div>
    </div>
</template>
<script>
    import { Toast } from 'mint-ui';
    export default {
    data:function(){
        return {
            lunbo: []
        }
    },
    created:function(){
        this.getlunbo();
    },
    methods:{
        getlunbo:function () {
            var url = "http://www.lovegf.cn:8899/api/getlunbo";
            this.$http.get(url).then(function (response) {
                var data = response.body;
                console.log(data);
                if (data.status != 0) {
                    Toast(data.message);
                    return;
                }
                this.lunbo = data.message;
            })
        }
    }
    }
</script>
<style scoped>
    .mint-swipe {
        height: 300px;
    }

    .mint-swipe-item {
        height: 300px;
        width: 100%;
        background-color: red;
    }

    .mint-swipe-item img {
        width: 100%;
        height: 100%;
    }

    .mui-content {
        background: white;
    }

    .mui-grid-view.mui-grid-9 {
        background: white;
        border-top: 0px;
        border-left: 0px;

    }

    .mui-grid-view.mui-grid-9 .mui-table-view-cell {
        border-right: 0px;
        border-bottom: 0px;
    }

    .mui-icon-home:before,
    .mui-icon-email:before,
    .mui-icon-chatbubble:before,
    .mui-icon-location:before,
    .mui-icon-search:before,
    .mui-icon-phone:before {
        content: "";
        display: inline-block;
        height: 50px;
        width: 50px;
        background-repeat: round;
    }

    .mui-icon-home:before {
        background-image: url(../../statics/images/1.png);
    }

    .mui-icon-email:before {
        background-image: url(../../statics/images/2.png);
    }

    .mui-icon-chatbubble:before {
        background-image: url(../../statics/images/3.png);
    }

    .mui-icon-location:before {
        background-image: url(../../statics/images/4.png);
    }

    .mui-icon-search:before {
        background-image: url(../../statics/images/5.png);
    }

    .mui-icon-phone:before {
        background-image: url(../../statics/images/6.png);

    }
</style>    