<template>
  <div class="p-2">
    <h1 class="text-2xl">Page Liste Supabase</h1>
  </div>
</template>

<script setup lang="ts">
import { supabase } from "../supabase";
console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code
const maisons = []; // à remplacer par l'appel à Supabase


</script>