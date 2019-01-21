<template>
  <div class="article-container">
    <section class="section">
      <div class="container">
        <div class="content"><Content/></div>
      </div>
    </section>
    <Toc/>
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
