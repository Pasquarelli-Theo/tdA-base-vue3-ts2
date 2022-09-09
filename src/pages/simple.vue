<template>
<div class="p-2">
    <h1 class="text-2xl">Page Simple</h1>
    <card class="w-1/2" v-bind="objet"/>
</div>
</template>

<script setup lang="ts">
    import card from "../components/card.vue";

    const objet = {nom:"Maison 1", price:256, favoris:false, txt:"Maison 1", nbbath:1, nbsize:"201m²", img:"/public/card.jpg"}
</script>