<template>
    <header class="flex items-center justify-between mb-10 border-b-2 border-gray-500">
        
        <h1>Task Master 📃</h1>
        
        <Button @click="$emit('add-task-button')">
            Add Task
        </Button>

    </header>
</template>

<script setup>
    import Button from './Button.vue'
</script>

