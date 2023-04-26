<template>
    <div class="w-full bg-gray-200 p-2 rounded-b-md">
        <div class="grid grid-cols-7 place-items-center gap-x-2 gap-y-4">
            <div v-for="day in days" :key="day">
                <span class="text-gray-500 font-semibold">
                    {{ day.substr(0,3) }}
                </span>
            </div>
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

const generateDatesForMonth = (m = dayjs().month(), y = dayjs().year()) => {
    dates.value = []
    let d = dayjs().month(m).year(y)

    const daysInMonth = d.daysInMonth()

    for(let i=0; i<= daysInMonth; i++) {
        // console.log("i", i)
        dates.value.push({
            date: i,
            day: d.date(i)
        })

    }
}

</script>

<style scoped>

</style>