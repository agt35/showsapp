<script setup>
import GOTCardsSuspense from './components/GOTCardsSuspense.vue';
import RickMortyCards from './components/RickMortyCards.vue';
import Hero from './components/Hero.vue';
import { ref } from 'vue';
const isGOT = ref(true);
</script>

<template>
  <main>
    <Hero :isGOT="isGOT" @selectShow="isGOT = !isGOT" />
    <GOTCardsSuspense v-if="isGOT" />
    <RickMortyCards v-else />
  </main>
</template>

<style scoped></style>


