<template>
  <div class="newsinfo-container">
      <h3 class="title">{{ newsinfo.title }}</h3>
      <p class="subtitle">
          <span>发表时间: {{ newsinfo.add_time | dateFormat }}</span>
          <span>点击: {{ newsinfo.click }}次</span>
      </p>
      <hr>
      <div class="content" v-html="newsinfo.content">

      </div>

      <!-- 评论子组件 -->
      <comment-box></comment-box>
  </div>
</template>

<script>
import comment from './comment.vue'

export default {
    data(){
        return {
            id: this.$route.params.id,
            newsinfo: {}
        }
    },
    created(){
        this.getNewsInfo()
    },
    methods: {
        getNewsInfo(){
            this.$http.get('api/getnew/' + this.id).then(result=>{
                if(result.body.status === 0){
                    this.newsinfo = result.body.message[0]
                } else{
                    Toast('获取新闻失败!')
                }
            })
        }
    },
    components: {
        "comment-box": comment
    }
}
</script>

<style lang="scss">
.newsinfo-container{
    padding: 0, 4px;
    .title{
        font-size: 1rem;
        text-align: center;
        margin: 0.9rem 0;
        color: red;
    }
    .subtitle{
        font-size: 0.7rem;
        color: blue;
        display: flex;
        justify-content: space-between;
    }
    .content{
        img{
            width: 100%;
        }
    }
}
</style>