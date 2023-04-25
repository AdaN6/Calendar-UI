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

type SelectedValues = {
    year: number
    month: number
}

const dateProps = defineProps<{
    selectedValues: SelectedValues
    selectedDate: number
}>()

const days = [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday"
]

</script>

<style scoped>

</style>