<script setup>
import GameCard from "../components/GameCard.vue";
import * as api from "../api/api.js";
import { onMounted, ref } from "vue";

const games = ref();
onMounted(async () => {
    games.value = await api.GamesCategory("battle-royale");
    console.log(games.value)
});
</script>

<template>
    <section>
        <h1 class="title">Royale</h1>
        <div class="block">
            <GameCard
            v-for="(item, index) in games" :key="index"
            :game="item"
                 />
        </div>
    </section>
</template>

<style scoped>
    .title {
        font-size: 40px;
        text-align: center;
        margin: 20px 0;
        color: white;
    }
    .block {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-gap: 50px;
        margin: 0 50px;
    }
</style>
