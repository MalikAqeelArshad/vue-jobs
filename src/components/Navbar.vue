<script setup>
import { RouterLink, useRoute } from 'vue-router';
import logo from '@/assets/img/logo.png';
import DropdownMenu from '@/components/DropdownMenu.vue';

const isActiveLink = (routePath) => {
  const route = useRoute();
  const isActive = route.path === routePath;
  return `${isActive ? 'bg-green-900' : ''} 'hover:bg-gray-900 hover:text-white text-white px-3 py-2 rounded-md`;
};
</script>

<template>
  <nav class="bg-green-700 border-b border-green-500 sticky top-0 z-50">
    <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
      <div class="flex h-20 items-center justify-between">
        <div class="flex flex-1 items-center justify-center sm:items-stretch sm:justify-start">
          <RouterLink to="/" class="flex flex-shrink-0 items-center mr-4">
            <img class="h-10 w-auto" :src="logo" alt="Vue Jobs" />
            <span class="hidden sm:block text-white text-2xl font-bold ml-2">Vue Jobs</span>
          </RouterLink>
          <div class="sm:ml-auto">
            <div class="flex space-x-2">
              <RouterLink to="/" :class="isActiveLink('/')">Home</RouterLink>
              <RouterLink to="/jobs" :class="isActiveLink('/jobs')">Jobs</RouterLink>
              <RouterLink to="/jobs/add" :class="isActiveLink('/jobs/add')">Add Job</RouterLink>
              <DropdownMenu />
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>
