<template>
  <div class="sidebar-container">
    <!-- TODO -->
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.sidebar-container {
  position: fixed;
  overflow: auto;
  -webkit-overflow-scrolling: touch;
  background-color: rgba(255,255,255,1);
  font-size: 0.9rem;
  padding: 1rem 1.4rem;
  z-index: 30;
  transition: all 400ms;
}
@media screen and (min-width: 752px) {
  .sidebar-container {
    top: 0;
    bottom: 0;
    right: 0;
    min-width: 300px;
    box-shadow: 0px 5px 30px 0px rgba(0,0,0,0.2);
  }
}
@media screen and (max-width: 751px) {
  .sidebar-container {
    top: 0;
    bottom: 0;
    right: 0;
    width: 65%;
    box-shadow: 0px 5px 30px 0px rgba(0,0,0,0.2);
  }
}
</style>
