<template>
  <div class="flex space-x-5" v-bind="$attrs">
      <div class="flex flex-col flex-grow">
        <Year @selected="changeYear"/>
        <Month @selected="changeMonth"/>
        <Dates :selectedValues="selectedValues" :selectedDate="selectedDateValue" @selected="changeDate" />
      </div>
    <div class="w-1/4 font-semibold">
        <span v-if="selectedDateValue"> 
              You have selected 
              <br>
              {{ `${selectedDateValue} - ${selectedValues.month + 1} - ${selectedValues.year}` }}
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
    // for the purpose of not showing value while changing either only month or year
  selectedDateValue.value = null
}

const changeMonth = (v) => {
  selectedValues.month = v
    // for the purpose of not showing value while changing either only month or year
  selectedDateValue.value = null
}

const changeDate = (v) => {
  selectedDateValue.value = v
}

</script>

<style>

</style>