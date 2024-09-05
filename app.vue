<template>
  <nav class="w-screen border-b py-4">
    <div class="container mx-auto flex items-center gap-10">
      <component v-for="item in menuItems" :key="item.key" :is="item.to ? NuxtLink : 'button'" v-bind="item"
        @click="item.onClick" class="flex items-center">
        <img v-if="item.image" :src="item.image" class="w-10 h-10 object-contain" />
        <component v-if="item.render" :is="item.render" />
        <component v-if="item.icon" :is="item.icon" :size="24" />
        <span v-if="item.title" class="ml-2">{{ item.title }}</span>
      </component>
    </div>
  </nav>
  <main class="h-64 bg-gray-100 flex justify-center pt-10 text-xl">App Here</main>
</template>

<script setup lang="jsx">
// Import necessary components
import { ref, computed } from "vue";
import { NuxtLink, Avatar } from "#components";
import { PhGauge, PhHouseSimple } from "@phosphor-icons/vue";

// Simulate user authentication status
const user = ref(true);

// Define menu items
const items = computed(() => [
  {
    key: "logo",
    image: "https://logo.clearbit.com/google.com",
    href: "/"
  },
  {
    icon: user.value ? PhGauge : PhHouseSimple,
    key: "dashboard",
    title: user.value ? "Dashboard" : "Home",
    to: user.value ? "/dashboard" : "/home",
  },
  {
    key: "spacer",
    class: "ml-auto",
  },
  {
    key: "add-funds",
    render: () => <span class="text-white bg-green-500 px-4 py-2 rounded-lg">Add Funds</span>
  },
  {
    key: "user",
    render: () => <Avatar src="https://randomuser.me/api/portraits/men/40.jpg" />,
    title: "Dubem Izuorah",
    hide: !user.value
  },
  {
    key: "auth",
    title: user.value ? "Logout" : "Login",
    onClick: () => user.value = !user.value
  },
]);

// Filter out hidden items
const menuItems = computed(() => items.value.filter(item => !item.hide));
</script>
