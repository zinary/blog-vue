<template>
  <div>
    <app-header></app-header>
    
   <router-view></router-view>
    

  </div>
</template>

<script>
import appHeader from './components/header';
export default {
  components: {
  'app-header':appHeader
  },
};
</script>

<style scoped>
* {
  font-family: monospace;
  font-size: 1rem;
}
</style>
