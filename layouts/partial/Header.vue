<template>
  <header class="header-container">
    <nav class="navbar is-primary">
      <div class="container">
        <div class="navbar-brand">
          <router-link :to="$site.base" class="navbar-item"><span class="site-brand">{{ $themeConfig.brand }}</span></router-link>
        </div>
        <div class="navbar-menu">
          <div class="navbar-end">
            <router-link class="navbar-item" v-for="item in $themeConfig.nav" :key="item.text" :to="item.link">{{ item.text }}</router-link>
            <a class="navbar-item" :href="githubLink" v-if="githubLink">GitHub</a>
          </div>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  computed: {
    githubLink: function() {
      return (
        this.$themeConfig.github ?
        "https://github.com/" + this.$themeConfig.github :
        null
      )
    }
  }
}
</script>

<style scoped>
.header-container {
  position: -webkit-sticky;
  position: sticky;
  top: 0px;
  z-index: 1000;
}
.site-brand {
  font-weight: bold;
}
</style>
