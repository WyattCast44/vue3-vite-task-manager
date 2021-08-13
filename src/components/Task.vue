<template>
    <div class="border-b my-4 pb-4 space-y-1 flex items-center justify-between">

        <div>

            <p>
                {{ task.body }}
            </p>

            <p class="text-xs" :class="(isPastDue() ? 'text-red-500' : 'text-gray-600')">
                {{ moment(props.task.date).fromNow() }}
            </p>

        </div>

        <button @click="$emit('delete-task', task.id)" class="px-3 hover:bg-red-300">
            Delete
        </button>
        
    </div>
</template>

<script setup>
import moment from 'moment'
import Button from './Button.vue'

const props = defineProps({
  task: Object
})

function isPastDue() {
    return (moment(props.task.date).diff(new Date(), 'days') < 0)
}

</script>