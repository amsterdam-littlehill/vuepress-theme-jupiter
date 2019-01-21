<template>
  <div class="article-container">
    <section class="section">
      <div class="container">
        <div class="content"><Content/></div>
      </div>
      <Toc v-if="$frontmatter.toc"/>
    </section>
  </div>
</template>

<script>
import Toc from '../partial/table-of-contents/Toc.vue'
export default {
  components: { Toc }
}
</script>

<style>

</style>
