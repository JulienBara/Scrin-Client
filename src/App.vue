<script setup lang="ts">
// import HelloWorld from './components/HelloWorld.vue'
import { ref, onMounted } from 'vue'

const gaufres = ref<{
  id: string;
  name: string;
}[]>([])

onMounted(() => {
  fetch(import.meta.env.VITE_BACKEND_URL+'/gaufres')
    .then((response) => response.json())
    .then((data) => {
      gaufres.value = data
    });
})

</script>

<template>
  <h1>Ils sont là aujourd'hui !</h1>
  <li v-for="gaufre in gaufres" :key="gaufre.id">
    {{ gaufre.name }}
  </li>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
