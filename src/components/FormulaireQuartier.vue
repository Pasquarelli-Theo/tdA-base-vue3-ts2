<script setup lang="ts">
import { supabase } from "@/supabase";
import { ref } from "@vue/reactivity";
import card from "../components/card.vue";
import { label } from "@formkit/inputs";
import { useRouter } from "vue-router";

const router = useRouter();
const Quartier = ref({});

const { data: libelle_Commune, error } = await supabase
  .from("Commune")
  .select("*");
if (error) console.log("n'a pas pu charger la table Commune :", error);

// Les convertir par `map` en un tableau d'objets {value, label} pour FormKit
const optionsCommune = libelle_Commune?.map((Commune) => ({
  value: Commune.code_Commune,
  label: Commune.libelle_Commune,
}));

const props = defineProps(["id"]);
if (props.id) {
  // On charge les donnÃ©es de la maison
  let { data, error } = await supabase
    .from("Quartier")
    .select("*")
    .eq("id", props.id);
  if (error) console.log("n'a pas pu charger le table quartier :", error);
  else Quartier.value = (data as any[])[0];
}

async function upsertquartier(dataForm, node) {
  const { data, error } = await supabase.from("Quartier").upsert(dataForm);
  if (error || !data) node.setErrors([error?.message]);
  else {
    node.setErrors([]);
    router.push({ name: "edit-id", params: { id: data[0].id } });
  }
}
</script>

<template>
  <div class="flex flex-wrap justify-center">
    <div class="p-2">
      <card v-bind="Quartier"></card>
    </div>
    <div class="">
      <div class="m-4">
        <!--on passe la ref a fromkit -->

        <FormKit
          class="bg-indigo-500"
          type="form"
          @submit="upsertquartier"
          v-model="Quartier"
          :submit-attrs="{}"
          :config="{
            classes: {
              input:
                'p-1 rounded  border-x-2 border-y-2 border-x-black border-y-black ',
              label: 'text-black',
            },
          }"
        >
          <FormKit
            class="p-7"
            name="libelle_Quartier"
            label="Quartier"
            type="text"
          />

          <FormKit
            name="favori"
            label="Mettre en valeur "
            type="checkbox"
            wrapper-class="flex"
            class="p-7"
          />
        </FormKit>
        <FormKit
          type="select"
          name="code_Commune"
          label="Commune"
          :options="optionsCommune"
        />
      </div>
    </div>
  </div>
</template>