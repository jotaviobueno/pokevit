<script>
  import navbar from './components/navbar.vue'

  export default {
    components: {
        navbar,
    },
  }
</script>

<template>
  <navbar />

  <div class="main">
    <router-view/>
  </div>

  <footer class="bg-primary text-light">
    <div>
    {{ new Date().getFullYear() }}
    </div>
  </footer>

</template>

<style scoped>

footer{
  position: fixed;
  bottom: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 56px;
}
</style>
