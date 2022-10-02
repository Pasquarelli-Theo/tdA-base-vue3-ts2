<script setup lang="ts">
import Card from "../components/card.vue";
import { supabase } from "../supabase";

console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code

let { data: Maison, error } = await supabase.from("Maison").select("*");
console.log(Maison);
</script>

<template>
  <div class="p-2">
    <h2 class="text-2xl font-bold underline text-red-500">Liste avec supabase</h2>
  </div>
  <div class="flex flex-row">
    <div v-for="m in Maison" :key="m">
      <Card v-bind="m"></Card>
    </div>
  </div>
</template>
