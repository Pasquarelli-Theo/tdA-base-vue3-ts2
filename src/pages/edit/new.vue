<script setup lang="ts">
import FormulaireOffreMaison from "../../components/FormulaireOffreMaison.vue";
</script>

<template>
  <div class="p-2">
    <h1 class="text-2xl">Page Formulaire</h1>
    <FormulaireOffreMaison v-bind="maison" />
  </div>
</template>
