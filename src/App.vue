<script setup lang="ts">
// import HelloWorld from './components/HelloWorld.vue'
import { ref, onMounted } from 'vue'

const gaufres = ref([])

onMounted(() => {
  fetch('http://127.0.0.1:8080/gaufres')
    .then((response) => response.json())
    .then((data) => {
      console.log(data)
      gaufres.value = data
    }).catch((err) => console.log(err));
})

</script>

<template>
  <h1>Ils sont là aujourd'hui!</h1>
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
