<template>
    <div class="mx-auto max-w-md py-4 px-8 bg-gray-800">
        <h2 class="text-lg text-center text-white">All Tasks</h2>
        <div v-for="task in tasks" :key="task.id">
            <Task @delete-task="$emit('delete-task', task.id)" :task="task" />
        </div>
    </div>
</template>

<script>
import Task from "./Task.vue"
export default {
    name: "List",
    props: {
        tasks: Array
    },
    components: {
        Task
    },
    emits: ["delete-task"]
}
</script>