<template>
  <div id="vuperess-theme-blog__tags-layout">
    <BlogTags :tags="$frontmatterKey.list"/>
  </div>
</template>
<style lang="stylus">
  #vuperess-theme-blog__tags-layout
    background #fff
    padding 20px
  @media(max-width: $MQNarrow)
    #vuperess-theme-blog__tags-layout
      margin-top 64px
      padding 30px
      height calc(100vh - 124px)
</style>