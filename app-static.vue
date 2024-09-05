<template>
  <nav class="w-screen border-b py-4">
    <div class="container mx-auto flex items-center gap-10">
      <!-- Logo -->
      <NuxtLink href="/" class="flex items-center">
        <img src="https://logo.clearbit.com/google.com" class="w-10 h-10 object-contain" />
      </NuxtLink>

      <!-- Dashboard or Home Link -->
      <NuxtLink v-if="user" href="/dashboard" class="flex items-center">
        <PhGauge size="24" />
        <span class="ml-2">Dashboard</span>
      </NuxtLink>
      <NuxtLink v-else href="/home" class="flex items-center">
        <PhHouseSimple size="24" />
        <span class="ml-2">Home</span>
      </NuxtLink>

      <!-- Spacer -->
      <div class="ml-auto"></div>

      <!-- Add Funds Button (Visible only when user is authenticated) -->
      <button v-if="user" class="flex items-center">
        <span class="text-white bg-green-500 px-4 py-2 rounded-lg">Add Funds</span>
      </button>

      <!-- User Avatar (Visible only when user is authenticated) -->
      <div v-if="user" class="flex items-center">
        <Avatar src="https://randomuser.me/api/portraits/men/40.jpg" />
        <span class="ml-2">Dubem Izuorah</span>
      </div>

      <!-- Auth Button -->
      <button class="flex items-center" @click="user = !user">
        <span>{{ user ? 'Logout' : 'Login' }}</span>
      </button>
    </div>
  </nav>
  <main class="h-64 bg-gray-100 flex justify-center pt-10 text-xl">App Here</main>
</template>

<script setup lang="jsx">
import { ref } from "vue";
import { NuxtLink, Avatar } from "#components";
import { PhGauge, PhHouseSimple } from "@phosphor-icons/vue";

// Simulate user authentication status
const user = ref(true);
</script>
