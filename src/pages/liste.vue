<template>
  <div class="p-2">
    <h1 class="text-2xl">Page Liste</h1>
    <div v-for="maisons in maisons" :key="maisons.nom">
      <card class="w-1/2" v-bind="maisons" />
    </div>
  </div>
</template>

<script setup lang="ts">
import card from "../components/card.vue";

const maisons = [
  {
    nom: "Maison 1",
    price: 256,
    favoris: false,
    txt: "Maison 1",
    nbbath: 1,
    nbsize: "201m²",
    img: "/public/card.jpg",
  },
  {
    nom: "Maison 2",
    price: 381,
    favoris: true,
    txt: "Maison 2",
    nbbath: 1,
    nbsize: "186m²",
    img: "/public/card.jpg",
  },
  {
    nom: "Maison 3",
    price: 524,
    favoris: false,
    txt: "Maison 3",
    nbbath: 3,
    nbsize: "193m²",
    img: "/public/card.jpg",
  },
  {
    nom: "Maison 4",
    price: 362,
    favoris: true,
    txt: "Maison 4",
    nbbath: 1,
    nbsize: "227m²",
    img: "/public/card.jpg",
  },
];
//   import maisons from "../assets/maisons.json";
</script>
