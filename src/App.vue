<script setup>
import GOTCards from './components/GOTCards.vue';
import RickMortyCards from './components/RickMortyCards.vue';


</script>

<template>
  <main>
    <h1>Hero</h1>
    <Suspense>
      <template #default>
        <GOTCards />
      </template>
      <template #fallback>
        <div>
          <p>Loading...</p>
        </div>
      </template>
    </Suspense>
    <RickMortyCards />
  </main>
</template>


