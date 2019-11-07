<template>
  <div id="base-list-layout">
    <div class="ui-posts">
      <div class="ui-post" v-for="page in pages">
        <div class="ui-post-title">
          <h2>{{ page.title }}</h2>
          <div class="ui-post-date" v-if="page.frontmatter.date">
            <ClockIcon/>
            <h2>{{ resovlePostDate(page.frontmatter.date) }}</h2>
          </div>
        </div>
        
        <div class="ui-post-summary" v-html="page.excerpt">
        </div>

        <div class="ui-post-author" v-if="page.frontmatter.author">
          <NavigationIcon/>
          <span>{{ page.frontmatter.author }} in {{ page.frontmatter.location }}</span>
        </div>
        <div class="ui-post-footer">
          <p><span v-for="item in page.frontmatter.tags">{{item}}</span></p>
          <NavLink :link="page.path">展开>></NavLink>
        </div>
      </div>
    </div>
    <component v-if="$pagination.length > 1 && paginationComponent" :is="paginationComponent"></component>
    <a style="float:right;height:36px;margin-top:20px;padding:5px 10px;" href="https://github.com/9240/vuepress-theme-similar-yilia.git">github</a>
  </div>
</template>

<script>
  /* global THEME_BLOG_PAGINATION_COMPONENT */
  
  import Vue from 'vue'
  import { NavigationIcon, ClockIcon } from 'vue-feather-icons'
  import { Pagination, SimplePagination } from '@vuepress/plugin-blog/lib/client/components'
  
  export default {
    components: { NavigationIcon, ClockIcon },

    data() {
      return {
        paginationComponent: null
      }
    },
    
    created() {
      this.paginationComponent = this.getPaginationComponent()
      console.log(this)
    },
    
    computed: {
      pages() {
        return this.$pagination.pages
      },
    },
    
    methods: {
      getPaginationComponent() {
        const n = THEME_BLOG_PAGINATION_COMPONENT
        if (n === 'Pagination') {
          return Pagination
        }

        if (n === 'SimplePagination') {
          return SimplePagination
        }

        return Vue.component(n) || Pagination
      },

      resovlePostDate(date) {
        return new Date(date.trim()).toDateString()
      }
    }
  }
</script>

<style lang="stylus">
  .common-layout
    .content-wrapper
      padding-bottom 80px
  
  .ui-post
    padding-bottom 25px
    margin-bottom 25px
    border-bottom 1px solid #f1f1f1

    background-color #fff
    padding 30px

    &:last-child
      border-bottom 0px
      margin-bottom 0px
    img
      width 60%
    p
      margin 0
  
  .ui-post-title
    display flex
    justify-content space-between
    align-items center
    font-family PT Serif, Serif
    /* font-size 28px */
    border-bottom 0
    /* color #808080 */
    h2
     border-bottom 0
  .ui-post-footer
    display flex
    justify-content space-between
    align-items center
    font-family PT Serif, Serif
    border-bottom 0
    color #fff
    span
      background-color #e2842a
      padding 4px
      border-radius 4px
    a
      cursor pointer
      transition all .2s
      text-decoration none
      background-color #000
      padding 5px
      color #fff
      &:hover
        text-decoration underline
  
  .ui-post-summary
    font-size 14px
    margin-bottom 15px
    color rgba(0, 0, 0, 0.54)
    font-weight 200
  
  .ui-post-author
    display flex
    align-items center
    font-size 12px
    line-height 12px
    color rgba(0, 0, 0, 0.84)
    margin-bottom 3px
    font-weight 400
    
    svg
      margin-right 5px
      width 14px
      height 14px
  
  .ui-post-date
    display flex
    align-items center
    font-size 12px
    color rgba(0, 0, 0, 0.54)
    font-weight 200
    
    svg
      margin-right 5px
      width 30px
      height 30px

@media (max-width: $MQMobile)
  .ui-post-title
    flex-direction column
  .ui-posts
    margin-top 60px
    img
      width 100%
</style>

<style src="prismjs/themes/prism-okaidia.css"></style>


