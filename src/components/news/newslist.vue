<template>
  <div id="tmpl">
        <ul class="mui-table-view">
            <li class="mui-table-view-cell mui-media" v-for="item in list">
                <a href="javascript:;">
                    <img class="mui-media-object mui-pull-left" :src="item.img_url">
                    <div class="mui-media-body">
                           {{item.title}}
                    <p class='mui-ellipsis' v-text="item.zhaiyao"></p>
                    </div>
                    <span>发布日期:{{item.add_time | datefmt("YYYY-MM-DD HH:mm:ss ")}}</span>
                    <span>点击数:{{item.click}}</span>
                </a>
            </li>
        </ul>
  </div>
</template>
<script>
import { Toast } from 'mint-ui';
export default {
  data(){
    return {
        list:[]
    }
  },
  created:function(){
    this.getNewsList();
  
     },
  methods:{
       getNewsList:function(){
        var url="http://www.lovegf.cn:8899/api/getnewslist";
        this.$http.get(url).then(function(resp){
            var data=resp.body;
            if(data.status !=0 ){
                Toast(data.message);
            }
            this.list=data.message;
        })
       }
     }
     
}

</script>
<style scoped>
.mui-table-view .mui-media-object{
    line-height: 80px;
    max-width: 80px; 
    height: 80px;
}
.mui-media-body{
    margin-bottom:1em;
}
.mui-media>a >span{
    font-size:14px;
    color:skyblue;
}
.mui-media>a >span:last-of-type{
    margin-left:20px;
}
</style>