<script setup lang="ts">
import { ref } from "@vue/reactivity";
import Card from "./card.vue";
// On fait une variable réactive qui réference les données
// ATTENTION : faire une Ref pas une Reactive car :
// c'est l'objet qui doit être réactif, pas ses props
const maison = ref({});
</script>
<template>
  <div>
    <div class="p-2">
      <h2 class="text-2xl">Résultat (Prévisualisation)</h2>
      <!-- Optionnel on affiche les données -->
      <Card v-bind="maison" />
    </div>
    <div class="p-2">
      <!-- On passe la "ref" à FormKit -->
      <FormKit
        type="form"
        :submit-attrs="{ classes: { input: 'bg-red-600 p-1 rounded' } }"
        :config="{
          classes: {
            input: 'p-1 rounded border-black shadow-sm border',
            label: 'text-gray-600',
          },
        }"
        v-model="maison"
      >
        <FormKit name="nom" label="Ville" />
        <FormKit name="txt" label="adresse" />
        <FormKit name="price" label="prix" type="number" />
        <FormKit
          name="favoris"
          label="mettre en favorie"
          type="checkbox"
          wrapper-class="flex"
        />
        <FormKit name="nbbath" label="nombre de salle de bain" />
        <FormKit name="nbsize" label="superficie" />
      </FormKit>
    </div>
  </div>
</template>