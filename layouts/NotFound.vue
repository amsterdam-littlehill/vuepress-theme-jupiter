<template>
  <div class="page-container">
    <div class="hero is-fullheight is-primary">
      <Header/>
      <div class="hero-body">
        <div class="container has-text-centered">
          <h1 class="title">404</h1>
          <p><router-link to="/">Go home</router-link></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './partial/Header.vue'
export default {
  components: { Header }
}
</script>

<style>

</style>
