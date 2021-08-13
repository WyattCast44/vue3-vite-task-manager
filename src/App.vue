<template>
    <Header @add-task-button="addTask" />

    <ul>
        <li v-for="task in tasks" :key="task.id">
            <Task :task="task" @delete-task="deleteTask" />
        </li>
    </ul>

</template>

<script setup>
import Header from './components/Header.vue'
import Task from './components/Task.vue'
</script>

<script>

export default {
    
    data() {
        return {
            tasks: [
                {
                    id: 1,
                    body: 'Learn VueJS 3',
                    date: '2021-08-14',
                },
                {

                    id: 2,
                    body: 'Learn InertiaJS',
                    date: '2021-08-01',
                },
            ]
        }
    },
    methods: {
        deleteTask(id) {
            this.tasks = this.tasks.filter((task) => task.id != id)            
        },
        addTask() { console.log('todo add') }
    }
}
</script>