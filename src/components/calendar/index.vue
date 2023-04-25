<template>
  <div class="flex space-x-5" v-bind="$attrs">
      <div class="flex flex-col flex-grow">
        <Year @selected="changeYear"/>
        <Month @selected="changeMonth"/>
        <Dates :selectedValues="selectedValues" :selectedDate="selectedDate"/> 
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
import { defineAsyncComponent, ref, reactive} from 'vue'
import dayjs from 'dayjs'

const Year = defineAsyncComponent(() => import('./Year.vue'))
const Month = defineAsyncComponent(() => import('./Month.vue'))
const Dates = defineAsyncComponent(() => import('./Dates.vue'))

const selectedDateValue = ref(dayjs().date())

// console.log(selectedDateValue)
// console.log(dayjs().date())
// console.log(ref(dayjs().date()))

const selectedValues = reactive({
  year: dayjs().year(),
  month: dayjs().month(),
})

const changeYear = (v) => {
  selectedValues.year = v

}

const changeMonth = (v) => {
  selectedValues.month = v
}

</script>

<style>

</style>