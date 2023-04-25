<script setup lang="ts">

import { defineAsyncComponent } from 'vue'

const Calendar = defineAsyncComponent(() => import('./components/calendar/index.vue'))

</script>

<template>
  <div>
    <h1 class="text-3xl font-bold underline">
    Hello world! 
  </h1>
  <Calendar />
  </div>
   
</template>

<style scoped>

</style>
