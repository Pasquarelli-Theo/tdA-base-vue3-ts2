<script setup lang="ts">
import { supabase } from "../supabase";

import FormulaireQuartier from "../components/FormulaireQuartier.vue";
import Card from "../components/card.vue";

console.log("supabase :", supabase);

let { data: quartier, error } = await supabase.from("quartier").select("*");
console.log(quartier);
</script>

<template>
  <h2 class="">Editer les quartier sur supabase</h2>
  <Card></Card>
  <FormulaireQuartier></FormulaireQuartier>
</template>
