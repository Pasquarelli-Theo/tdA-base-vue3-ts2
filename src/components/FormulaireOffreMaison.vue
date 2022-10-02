<script setup lang="ts">
import { supabase } from "@/supabase";
import { ref } from "@vue/reactivity";
import { useRouter } from "vue-router";
import Card from "./card.vue";
// On fait une variable réactive qui réference les données
// ATTENTION : faire une Ref pas une Reactive car :
// c'est l'objet qui doit être réactif, pas ses props
const router = useRouter();
 const Maisons = ref({});

const props = defineProps(["id"]);
if (props.id) {
    // On charge les données de la maison
    let { data, error } = await supabase
        .from("Maison")
        .select("*")
        .eq("id", props.id);
    if (error) console.log("n'a pas pu charger le table Maison :", error);
    else Maisons.value = (data as any[])[0];
}


async function upsertMaison(dataForm, node) {
    const { data, error } = await supabase.from("Maisons").upsert(dataForm);
    if (error || !data) node.setErrors([error?.message])
    else {
        node.setErrors([]);
        router.push({ name: "edit-id", params: { id: data[0].id } });
    }
}
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
        :submit="upsertMaison"
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