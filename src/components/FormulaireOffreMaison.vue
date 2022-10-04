<script setup lang="ts">
    import { supabase } from "@/supabase";
    import { ref } from "@vue/reactivity";
    import { useRouter } from "vue-router";
    import Card from "./card.vue";
    const router = useRouter();
  const props = defineProps(["id"]);
if (props.id) {
    // On charge les données de la maison
    let { data: Maison, error } = await supabase
        .from("Maison")
        .select("*")
        .eq("id_maison", props.id);
    if (error) console.log("n'a pas pu charger le table Maison :", error);
    else Maison.value = (data as any[])[0];
}
    async function upsertMaison(dataForm, node) {
    const { data, error } = await supabase.from("Maison").upsert(dataForm);
    if (error || !data) node.setErrors([error?.message])
    else {
    node.setErrors([]);
    router.push({ name: "edit-id", params: { id_maison: data[0].id} });
    }
}
</script>

<template>
    <div>
        <div class="p-2">
            <h2 class="text-2xl">Résultat (Prévisualisation)</h2>
            <!-- Optionnel on affiche les données -->
            <Card v-bind="Maison" />

        </div>
        <div class="p-2">
            <!-- On passe la "ref" à Formkit -->
            <FormKit type="form" v-model="Maison" @submit="upsertMaison"
            :config="{
                        classes: {
                                    input: 'p-1 rounded shadow-sm border bg-gray-100',
                                    label: 'text-gray-600',
                                },
                    }"
            :submit-attrs="{ classes: { input: 'bg-red-600 mt-2 px-6 py-2 rounded-full text-center' } }">
                <FormKit name="nom" label="Nom"/>
                <FormKit name="txt" label="Adresse"/>
                <FormKit name="price" label="Prix" type="number"/>
                <FormKit name="img" label="Image"/>
                <FormKit name="nbsize" label="Superficie"/>
                <FormKit name="nbbath" label="Nombre de salle de bains" type="number"/>
                <!-- <FormKit name="favoris" label="mettre en valeur" type="checkbox" wrapper-class="flex gap-4"/> -->
            </FormKit>
        </div>
    </div>
</template>