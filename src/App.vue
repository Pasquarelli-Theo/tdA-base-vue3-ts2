<template>
  <nav class="bg-black">
    <h4 class="text-xl">
      <Bars3Icon class="inline-block ml-2 h-5 w-5 text-red-300" />
      menu (dans <code class="font-mono">/src/App.vue</code>)
    </h4>
    <ul class="ml-2">
      <li>
        <router-link class="text-white underline hover:text-red-400" to="/">
          <code class="font-mono">Home</code>
        </router-link>
      </li>
      <h2 class="text-white text-2xl mt-2 mb-2"> TP01</h2>
      <li>
        <router-link class="text-white underline hover:text-red-400" to="/simple">
          <h2>Page Simple</h2>
        </router-link>
      </li>
      <li>
        <router-link class="text-white underline hover:text-red-400" to="/liste">
          <h2>Page Liste</h2>
        </router-link>
      </li>
      <li>
        <router-link class="text-white underline hover:text-red-400" to="/liste-fetch">
          <h2>Page Liste-Fetch</h2>
        </router-link>
      </li>
      <h2 class="text-white text-2xl mt-2 mb-2"> TP02</h2>
      <li>
        <router-link class="text-white underline hover:text-red-400" to="/edit/new">
          <h2>Page Formulaire</h2>
        </router-link>
      </li>
      <h2 class="text-white text-2xl mt-2 mb-2"> TP03</h2>
      <li>
        <router-link class="text-white underline hover:text-red-400" to="/liste-supabase">
          <h2>Page Supabase</h2>
        </router-link>
      </li>
      <li>
        <router-link class="text-white underline hover:text-red-400" to="/login-logout">
          <h2>Login</h2>
        </router-link>
        <h2 class="text-white text-2xl mt-2 mb-2"> TP04</h2>
        <router-link class="text-white underline hover:text-red-400" to="/indexQuartier">
          <h2>Quartier</h2>
        </router-link>
        <router-link class="text-white underline hover:text-red-400" to="/edition">
          <h2>edit</h2>
        </router-link>
        
      </li>
    </ul>
  </nav>

  <!-- Affiche les pages -->
  <Suspense> <router-view class="m-2 border-2 p-2" /></Suspense>
</template>

<script setup lang="ts">
import { Bars3Icon } from "@heroicons/vue/20/solid";
</script>