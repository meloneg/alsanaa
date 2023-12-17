<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import sidebar from '@/components/sidebar.vue'
import Footer from '@/components/footer.vue'
</script>

<template>
  <header>
    <sidebar />
    <AppImage class="logo" :size="{ width: 250 }" src="elsan3a.png"></AppImage>
    <div class="view-wrapper">
      <RouterView />
    </div>
    <Footer />
  </header>
</template>

