<template>
  <main class="page">
    <slot name="top" />

    <div class="theme-default-content content__default">
      <div class="summary">
        <div style="display:flex;justify-content:space-between;border-bottom: 1px solid #eaecef;">
          <h2 style="border-bottom:none;background: #fff;padding: 1rem 2.5rem;">{{this.$page.title}}</h2>
          <h2 style="color:#ada7a7;border-bottom:none;background: #fff;padding: 1rem 2.5rem;">{{this.$page.frontmatter.date.split("T")[0]}}</h2>
        </div>
        <Content class="theme-default-content" />
      </div>
    </div>
    <PageEdit />

    <PageNav v-bind="{ sidebarItems }" />

    <slot name="bottom" />
  </main>
</template>

<script>
import PageEdit from '@theme/components/PageEdit.vue'
import PageNav from '@theme/components/PageNav.vue'

export default {
  components: { PageEdit, PageNav },
  props: ['sidebarItems'],
}
</script>

<style lang="stylus">
@require '../styles/wrapper.styl'

.page
  padding-bottom 2rem
  display block

</style>
