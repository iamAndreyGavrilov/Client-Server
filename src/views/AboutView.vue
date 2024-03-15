<template>
  <div class="about">
    <ClientServer />
  </div>
</template>

<style lang="scss">
@media (min-width: 1024px) {
  .about {
    //min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
<script setup lang="ts">
import ClientServer from '@/components/clientServerApp/ClientServer.vue'
</script>
