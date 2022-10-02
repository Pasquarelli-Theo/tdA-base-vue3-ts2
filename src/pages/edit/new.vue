<script setup lang="ts">
import FormulaireOffreMaison from "../../components/FormulaireOffreMaison.vue";
</script>

<template>
  <div class="p-2">
    <h2 class="text-2xl font-bold underline text-red-500">Page Formulaire</h2>
    <FormulaireOffreMaison v-bind="maison" />
  </div>
</template>
