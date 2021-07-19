<template>
    <form class="mx-auto mb-2 px-8 py-4 max-w-md flex-col items-center border-solid bg-gray-800 text-white text-black" action="">
        <div class="flex justify-between mt-2">
            <label for="task">Task</label>
            <input class="border-2 border-solid bg-gray-200 rounded-2xl text-black" type="text" name="task" id="task">
        </div>
        <div class="flex justify-between mt-2">
            <label for="des">Description</label>
            <input class="border-2 border-solid bg-gray-200 rounded-2xl text-black" type="text" name="des" id="des">
        </div>
        <div class="flex justify-between mt-2">
            <label for="category">Category</label>
            <select class="bg-gray-200 rounded-2xl text-black" name="type" id="option">
                <option value="">Select a type</option>
                <option value="work">Work</option>
                <option value="home">Home</option>
            </select>
        </div>
        <div class="flex items-baseline justify-between">
            <label for="completed" id="completed">Completed: </label>
            <Switch @click=setComplete />
        </div>
        <div>
            <input @click="submitHandler" class="mx-auto py-1 px-2 w-3/6 bg-black text-white rounded-2xl" type="submit" value="Add Task">
        </div>
    </form>
</template>

<script>
import Switch from './Switch.vue';

export default {
    name: 'Form',
    data() {
        return {
            option: false
        }
    },
    components: {
        Switch,
    },
    methods: {
        setComplete() {
            this.option = !this.option
        },
        submitHandler (e) {
            e.preventDefault();

            const task = document.querySelector("#task");
            const des = document.querySelector("#des");
            const option = document.querySelector("#option");
            const completed = this.option;

            if (task.value == "" && des.value === ""){
                return;
            }

            const newTask = {
                task: task.value,
                des: des.value,
                category: option.value,
                completed: completed
            }

            this.$emit("add-task", newTask);
            
            task.value = "";
            des.value = "";
            completed.value = false;
        }
    },
    emits: ["completed"]
}
</script>
