<template>
  <div class="p-2">
    <h2 class="text-2xl font-bold underline text-red-500">Page Liste Fetch</h2>
    <div v-for="maisons in maisons" :key="maisons.nom">
      <card class="w-1/2" v-bind="maisons" />
    </div>
  </div>
</template>

<script setup lang="ts">
import card from "../components/card.vue";

const res = await fetch("maisons.json");
const maisons = await res.json();
</script>