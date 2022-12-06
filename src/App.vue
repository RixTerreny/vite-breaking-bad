<script>
export default{
  components: {Page},
}
import 'bootstrap/dist/css/bootstrap.min.css'
import Page from './components/Page.vue';
</script>

<template>
<div class="text-white">
  <h1 class="ms-3 mt-2">Breacking Wars Api</h1>
</div>
<Page/>
</template>

<style lang="scss">
@use './styles/general.scss' as *;
body{
  background-color: $main;
}
</style>
