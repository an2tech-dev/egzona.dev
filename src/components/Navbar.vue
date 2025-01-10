<template>
    <nav class="bg-white dark:bg-darkBlue text-gray-900 dark:text-white shadow-lg border-b border-gray-200 dark:border-gray-600">
      <div class="container mx-auto flex items-center justify-between py-4 px-6">
        <div class="flex items-center">
          <span class="font-bold text-lg">egzona.dev</span>
        </div>
    
        <ul class="hidden lg:flex lg:space-x-6">
          <li>
            <router-link to="/" class="hover:text-blue-500 dark:hover:text-blue-300">Homes</router-link>
          </li>
          <li>
            <router-link to="/pages" class="hover:text-blue-500 dark:hover:text-blue-300">Pages</router-link>
          </li>
          <li>
            <router-link to="/landing" class="hover:text-blue-500 dark:hover:text-blue-300">Landing</router-link>
          </li>
          <li>
            <router-link to="/blog" class="hover:text-blue-500 dark:hover:text-blue-300">Blog</router-link>
          </li>
          <li>
            <router-link to="/widgets" class="hover:text-blue-500 dark:hover:text-blue-300">Widgets</router-link>
          </li>
        </ul>
    
        <div class="flex items-center space-x-4">
          <button
            @click="toggleTheme"
            class="p-2 border border-gray-300 dark:border-gray-600 rounded-full"
          >
            <span v-if="isDarkMode" class="material-icons">light_mode</span>
            <span v-else class="material-icons">dark_mode</span>
          </button>
          <button
            @click="isMenuOpen = !isMenuOpen"
            class="lg:hidden p-2 rounded-md border border-gray-300 dark:border-gray-600"
          >
            <span v-if="isMenuOpen" class="material-icons">close</span>
            <span v-else class="material-icons">menu</span>
          </button>
        </div>
      </div>
    
      <ul
        :class="[
          'lg:hidden',
          isMenuOpen ? 'block' : 'hidden',
          'absolute top-16 left-0 w-full bg-white dark:bg-darkBlue shadow-lg text-center',
        ]"
      >
        <li>
          <router-link to="/" class="block py-2 hover:text-blue-500 dark:hover:text-blue-300">Homes</router-link>
        </li>
        <li>
          <router-link to="/pages" class="block py-2 hover:text-blue-500 dark:hover:text-blue-300">Pages</router-link>
        </li>
        <li>
          <router-link to="/landing" class="block py-2 hover:text-blue-500 dark:hover:text-blue-300">Landing</router-link>
        </li>
        <li>
          <router-link to="/blog" class="block py-2 hover:text-blue-500 dark:hover:text-blue-300">Blog</router-link>
        </li>
        <li>
          <router-link to="/widgets" class="block py-2 hover:text-blue-500 dark:hover:text-blue-300">Widgets</router-link>
        </li>
      </ul>
    </nav>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  
  const isDarkMode = ref(false);
  const isMenuOpen = ref(false);
  
  const toggleTheme = () => {
    isDarkMode.value = !isDarkMode.value;
    const root = document.documentElement;
    root.classList.toggle('dark', isDarkMode.value);
    localStorage.setItem('darkMode', isDarkMode.value);
  };
  
  onMounted(() => {
    isDarkMode.value = localStorage.getItem('darkMode') === 'true';
    const root = document.documentElement;
    root.classList.toggle('dark', isDarkMode.value);
  });
  </script>