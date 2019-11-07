<template>
  <div id="vuperess-theme-blog__post-layout">
    <div class="vuepress-blog-theme-content">
      <h2>{{this.$page.title}}</h2>
      <Content/>
      <hr/>
      <Comment/>
    </div>
    <Toc/>
  </div>
</template>

<script>
  import Toc from '@theme/components/Toc.vue'
  import { Comment } from '@vuepress/plugin-blog/lib/client/components'
  
  export default {
    components: {
      Toc,
      Comment,
    },
    created() {
      console.log(this)
    },
  }
</script>

<style lang="stylus">
@require '../styles/wrapper.styl';
  .vuepress-blog-theme-content
    @extend $wrapper
    font-size 16px
    letter-spacing 0px
    font-family PT Serif, Serif
    color #2c3e50
    position relative

@media(max-width: $MQNarrow)
  .vuepress-blog-theme-content
    margin-top: 64px;
</style>

<style src="prismjs/themes/prism-okaidia.css"></style>

