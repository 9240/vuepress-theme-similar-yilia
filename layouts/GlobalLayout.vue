<template>
  <div id="vuperess-theme-blog__global-layout">
    <MobileHeader :isOpen="isMobileHeaderOpen" @toggle-sidebar="isMobileHeaderOpen = !isMobileHeaderOpen"/>
    <div class="left link" :class="{showLink:isShow}">
      <div class="search-wrap">
        <input type="text" class="search-input" placeholder="search..." v-model="searchVal">
      </div>
      <ul class="search-ul">
        <li class="search-li" v-for="item in searchRes">
          <a class="search-title" :href="item.path"><span >{{item.title}}</span></a>
          <p class="search-time">
            <ClockIcon />
            <span>{{item.frontmatter.date.split('T')[0]}}</span><span v-for="tag in item.frontmatter.tags">{{tag}}</span>
          </p>
        </li>
      </ul>
    </div>
    <div class="left msg" :class="{show:isShow}">
      <div class="overlay"></div>
      <div class="intrude-less">
        <header id="header" class="inner">
          <a href="/" class="profilepic">
            <img :src="this.$themeConfig.avator" class="js-avatar">
          </a>
          <hgroup>
            <h1 class="header-author"><a href="/">{{this.$themeConfig.name}}</a></h1>
          </hgroup>
          <p class="header-subtitle">{{this.$themeConfig.desc}}</p>
          <nav class="header-menu">
            <ul>
              <li v-for="(val,key) in this.$themeConfig.menu"><a :href="val">{{key}}</a></li>
            </ul>
          </nav>
          <nav class="header-smart-menu">
              <a href="javascript:void(0)" v-on:click="showLink">所有文章</a>
          </nav>
          <nav class="header-nav">
            <div class="social">
              <a class="github" target="_blank" href="https://github.com/litten" title="github"><i class="icon-github"></i></a>
              <a class="weibo" target="_blank" href="http://weibo.com/litten225" title="weibo"><i class="icon-weibo"></i></a>
              <a class="rss" target="_blank" href="/atom.xml" title="rss"><i class="icon-rss"></i></a>
            </div>
          </nav>
        </header>		
      </div>
    </div>
    <div class="container" v-on:click="closeLink" >
      <div class="content-wrapper" @click="isMobileHeaderOpen = false" :class="{hideSome:isShow}">
        <DefaultGlobalLayout/>
      </div>
    </div>
  </div>
</template>

<script>
  import GlobalLayout from '@app/components/GlobalLayout.vue'
  import MobileHeader from '@theme/components/MobileHeader.vue'
  import { NavigationIcon, ClockIcon } from 'vue-feather-icons'
  export default {
    components: {
      DefaultGlobalLayout: GlobalLayout,
      MobileHeader,
      ClockIcon
    },

    data() {
      return {
        isMobileHeaderOpen: false,
        leftLink:[],
        isShow:false,
        searchVal:""
      }
    },

    mounted() {
      this.$router.afterEach(()=>{
        this.isMobileHeaderOpen = false
      })
      var compare = function (x, y) {
        if (x.path < y.path) {
          return 1;
        } else if (x.path > y.path) {
          return -1;
        } else {
          return 0;
        }
      }
      this.leftLink = this.$site.pages.filter(item=>{
        return item.excerpt
      }).sort(compare)
    },
    methods:{
      showLink(){
        this.isShow = true
      },
      closeLink(){
        this.isShow = false
      }
    },
    computed: {
      searchRes(){
        return this.leftLink.filter(item=>{
          return item.title.includes(this.searchVal)
        })
      }
    },
  }
</script>

<style lang="stylus">
  .left
    position fixed
    left 0
    width 300px
    height 100%
    background-color #fff
  .msg
    z-index 999
    .overlay
      width 300px
      height 180px
      position absolute
      background-color #0ff
    .intrude-less 
      width 76%
      text-align center
      margin 112px auto 0
      #header 
        width 100%
        height 300px
        position relative
        border-bottom 1px solid color-border
        text-align center
        .profilepic 
          display block
          border 5px solid #fff
          border-radius 300px
          width 128px
          height 128px
          margin 0 auto
          position relative
          overflow hidden
          background #88acdb
          img 
            border-radius 300px
            opacity 1
            width 100%
        .header-subtitle
          color #999
          font-size 14px
          line-height 25px
          overflow hidden
          text-overflow ellipsis
        .header-menu
          font-weight 300
          line-height 31px
          text-transform uppercase
          float none
          min-height 150px
          margin-left -12px
          text-align center
        .header-smart-menu
          font-size 12px
          margin-bottom 20px
  .link
    z-index 1
    overflow hidden
    overflow-y auto
    .search-ul
      .search-li
        line-height 1

        .search-time
          display flex
          align-items center
          margin-top 2px
          border-bottom 1px dotted
          span
            margin-left:10px
            font-size 14px
          svg
            width 14px
            height 14px
            padding 5px
    a
      cursor pointer
      transition all .2s
      text-decoration none
      padding 5px
      font-size 18px
      color #000
      &:hover
        color #000
    .search-wrap
      width 280px
      padding-left 10px
      margin 20px 0 20px 10px
      position relative
      .search-input
        width 100%
        border none
        border-bottom 1px solid
        outline none
        height 30px
  .show
    box-shadow 0 0 6px 0 rgba(0,0,0,.75)
  .showLink
    left 300px
  .hideSome
    margin-left 300px
  .container
    width calc(100vw - 300px)
    position absolute
    right 0px
    min-height 100%
    background-color #eee
    overflow hidden
      
  .content-wrapper
    padding 40px 40px 80px 40px
    min-height calc(100vh - 80px - 60px - 160px)
    width calc(100vw - 400px)

  @media (max-width: $MQMobile)
    .left
      display none
    .container
      width 100vw
      position static
      background-color #eee
    .content-wrapper
      padding 0
      min-height calc(100vh - 20px - 60px - 100px)
      width 100%
</style>
