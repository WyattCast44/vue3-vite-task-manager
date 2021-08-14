<template>
    <div class="absolute bottom-0 left-0 right-0 flex items-center justify-center" v-show="show">
        <div class="w-80 mx-auto px-12 pb-8 pt-4 rounded-t border border-gray-400 bg-white shadow">
            <h2>Add a Task</h2>
            <input type="text" placeholder="Task" class="w-full" autofocus v-model="task.body">
            <input type="date" placeholder="Date" class="w-full" v-model="task.date">
            <button class="w-full hover:bg-green-300"
                v-on:click="emitTaskAdded">
                Add
            </button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            task: {}
        }
    },
    props: {
        show: Boolean,
    },
    methods: {
        emitTaskAdded() {
            
            if(this.task.body.trim() == "") {
                this.task.body = ""
                return;
            }

            this.$emit('task-added', this.task.body, this.task.date)

            this.task = {}
        }
    }  
}
</script>