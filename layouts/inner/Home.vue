<template>
  <div class="home-container">
    <section class="hero is-primary">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">{{ $site.title }}</h1>
          <p class="subtitle">{{ $site.description }}</p>
        </div>
      </div>
    </section>
    <section class="section">
      <div class="container">
        <div class="content"><Content/></div>
      </div>
    </section>
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>
