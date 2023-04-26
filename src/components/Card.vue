<script setup>
import { defineProps } from 'vue';

const { name, image, title } = defineProps(['image', 'name', 'title'])
</script>

<template>
    <n-card>
        <template #cover>
            <img :src="image">
        </template>
        <h3>{{ name }}</h3>
        <h4>{{ title }}</h4>
    </n-card>
</template>


<style scoped>
.n-card {
    width: 200px;
    margin: 10px 20px;
}

.n-card img {
    height: 250px
}

p {
    font-size: 10px;
}
</style>