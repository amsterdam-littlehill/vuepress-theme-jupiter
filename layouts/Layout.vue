<template>
  <div class="page-container">
    <Header/>
    <Home v-if="$frontmatter.layout=='home'"/>
    <Content v-else/>
  </div>
</template>

<script>
import dayjs from 'dayjs'

import Header from './partial/Header.vue'
import Home from './inner/Home.vue'

export default {
  components: { Header, Home },
  created: function() {
    // Convert date string to dayjs object
    this.$site.pages.forEach(page => {
      page.date = page.frontmatter.date ?
        dayjs(page.frontmatter.date) :
        dayjs(page.lastUpdated)
    })
  },
}
</script>

<style src="@fortawesome/fontawesome-free/css/all.min.css"></style>
<style src="bulma-jupiter/dist/bulma-jupiter.min.css"></style>
<style src="../styles/fix.css"></style>

<style>
@import url("https://fonts.proxy.ustclug.org/css?family=IBM+Plex+Sans:400,400i,600,600i|IBM+Plex+Mono");
</style>
