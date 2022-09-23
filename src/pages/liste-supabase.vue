<script setup lang="ts">
import { supabase } from "../supabase";
console.log("supabase :", supabase); // pour vérifier et "garder" supabase dans le code

let { data: Maison, error } =
await supabase
.from('Maison').
select("*")
console.log('maison :',Maison)

</script>

<template>
  <div class="p-2">
    <h1 class="text-2xl">Page Liste Supabase</h1>
  </div>
</template>