<template>
  <div class="flex space-x-5" v-bind="$attrs">
      <div class="flex flex-col flex-grow">
        <Year />
        <Month />
        <Dates /> 
    </div>
    <div class="w-1/4 ">
        <span v-if="selectedDateValue"> 
              You have selected 
              <br>
              {{ `${selectedDateValue} -` }}
          </span>
    </div> 
  </div>
</template>

<script setup lang="ts">
import { defineAsyncComponent, ref } from 'vue'
import dayjs from 'dayjs'

const Year = defineAsyncComponent(() => import('./Year.vue'))
const Month = defineAsyncComponent(() => import('./Month.vue'))
const Dates = defineAsyncComponent(() => import('./Dates.vue'))

const selectedDateValue = ref(dayjs().date())

console.log(selectedDateValue)
console.log(dayjs().date())
console.log(ref(dayjs().date()))

</script>

<style>

</style>