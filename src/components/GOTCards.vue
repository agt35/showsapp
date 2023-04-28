<script setup>
import axios from 'axios';
import { ref, watch } from 'vue';
import Card from './Card.vue';

const characters = ref(null);
const page = ref(0);

const response = await axios.get(`https://thronesapi.com/api/v2/Characters`);
characters.value = response.data.splice(page.value * 8, 8);

watch(page, async () => {
    const res = await axios.get(`https://thronesapi.com/api/v2/Characters`);
    const data = res.data.splice(page.value * 8, 8);
    characters.value = data;
})


</script>

<template>
    <div class="container">
        <div class="cards">
            <Card v-for="char in characters" :image="char.imageUrl" :name="char.fullName" :key="char.id">
                <div>
                    <h4>{{ char.title }}</h4>
                </div>
            </Card>
        </div>
        <div class="button-container">
            <button @click="page--" :disabled="page === 0">&lt</button>
            <button @click="page++">&gt</button>
        </div>
    </div>
</template>

<style scoped>
.container {
    background-color: rgb(27, 26, 26);
    padding: 30px
}

.cards {
    max-width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    height: 700px
}

.cards h3 {
    font-weight: bold;
}

.cards p {
    font-size: 10px;
}

.jobs {
    display: flex;
    flex-wrap: wrap;
}

.button-container {
    display: flex;
    justify-content: center;
    padding-top: 30px
}

.button-container button {
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 100%;
    margin: 0 5px;
    cursor: pointer;
}

.spinner {
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>