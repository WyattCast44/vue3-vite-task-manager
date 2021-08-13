<template>

    <Header @add-task-button="showTaskAdder" />

    <ul>
        <li v-for="task in tasks" :key="task.id">
            <Task :task="task" @delete-task="deleteTask" />
        </li>
    </ul>

    <add-task-drawer :show="showDrawer" @task-added="addTask" />

</template>

<script setup>
import Header from './components/Header.vue'
import Task from './components/Task.vue'
import AddTaskDrawer from './components/AddTaskDrawer.vue'
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
            ], 
            showDrawer: false
        }
    },
    methods: {
        deleteTask(id) {
            this.tasks = this.tasks.filter((task) => task.id != id)            
        },
        showTaskAdder() { 
            this.showDrawer = ! this.showDrawer
        },
        addTask(name, date) { 
            this.tasks.push({
                id: this.tasks.length + 1, 
                body: name, 
                date: date,
            })
        }
    }
}
</script>