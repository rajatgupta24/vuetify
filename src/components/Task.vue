<template>
  <div class="w-full px-4 pt-8">
    <div class="w-full max-w-md mx-auto bg-gray-800 rounded-2xl">
      <Disclosure v-show="open">
        <DisclosureButton
            @click="setOpen"
            class="flex justify-between w-full px-4 py-2 text-sm font-medium text-left bg-gray-200  focus:outline-none focus-visible:ring focus-visible:ring-purple-500 focus-visible:ring-opacity-75"
        >
          <span :class="task.completed ? 'line-through' : 'text-black'">{{task.task}}</span>
          <button @click="Delete(task.id)">Delete</button>
        </DisclosureButton>
        <DisclosurePanel v-show="open" class="px-4 pt-2 pb-2 text-sm text-black bg-gray-300">
            <h3>{{task.des}}</h3>
        </DisclosurePanel>
      </Disclosure>
    </div>
  </div>
</template>

<script>
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue';
// import Modal from "./Modal.vue";

export default {
    name: "Task",
    data() {
        return {
            open: false,
        }
    },
    props: {
        task: Object
    },
    methods: {
        setOpen() {
            this.open = !this.open
        },
        Delete(id) {
            this.$emit("delete-task", id);
        }
    },
    components: {
        Disclosure,
        DisclosureButton,
        DisclosurePanel,
        // Modal
    },
}
</script>
