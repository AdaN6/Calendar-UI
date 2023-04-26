<template>
    <div class="w-full bg-gray-200 p-3 rounded-b-md">
        <div class="grid grid-cols-7 place-items-center gap-x-2 gap-y-4">
            <div v-for="day in days" :key="day">
                <span class="text-gray-500 font-semibold">
                    {{ day.substr(0,3) }}
                </span>
            </div>


            <!-- use nested for loop if the index is 0 put the black spaces  -->
            <template v-for="(d, index) in dates" :key="d">
                <template v-if="index == 0" >
                    <div v-for="i in d.day" :key="i">
                    </div>
                </template>

                <!-- use bind class ":class" for showing select and non-select date colour bg  -->
                <button class="w-9 h-9 rounded-full flex items-center justify-center text-sm font-semibold"
                @click="selected(d.date)"
               
                :class="{
                    'bg-black text-blue-100': (d.date == dayjs().date() && dateProps.selectedValues.month == dayjs().month() 
                    && dateProps.selectedValues.year == dayjs().year()),
                    'bg-emerald-500 text-gray-50 ring ring-green-700': d.date == date,
                    'bg-gray-300': d.date != date
                 }">

                
                    <span>
                        {{ d.date }}
                    </span>
                </button>
            </template>


        </div>
    </div>
</template>

<script setup lang="ts">

import {watch, onMounted, ref} from "vue"
import dayjs from "dayjs"

type SelectedValues = {
    year: number
    month: number
}

type Date = {
    day: number
    date: number
}

const dateProps = defineProps<{
    selectedValues: SelectedValues
    selectedDate: number
}>()

const dates = ref<Date[]>([])

onMounted(() => {
    generateDatesForMonth()
})

// --- WATCH: when the month and year change date also change ---
// 1st watch the selectedValues
watch(() => dateProps.selectedValues, (v) => {
    // for everytime when someone change the calendar the value will still there 
    date.value = null
    generateDatesForMonth(v.month, v.year)
}, {
    // deep watch is if only changing one key and not changing entire object, the watch "dateProps.selectedValues" won't run
    deep: true
})

// create array of days

const days = [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday"
]

const generateDatesForMonth = (m = dayjs().month(), y = dayjs().year()) => 
{
    dates.value = []
    let d = dayjs().month(m).year(y)

    const daysInMonth = d.daysInMonth()

    for(let i=1; i <= daysInMonth; i++) {
        // console.log("i", i)
        dates.value.push({
            date: i,
            day: d.date(i).day()
        })

    }
    // console.log(dates.value)
}


//  ---- for selected date ----

const date = ref<number>(null)

// we need Emit to pass the selected date
const dateEmit = defineEmits<{ (e: 'selected', v: number): void }>()

// funtion for selected date
const selected = (d) => {
    date.value = d
    dateEmit('selected', d)
}



</script>

<style scoped>

</style>