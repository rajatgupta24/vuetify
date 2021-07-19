<template>
  <div class="py-2">
    <Switch
      v-model="enabled"
      :class="enabled ? 'block bg-green-900 w-8 h-5 rounded-full' : 'block bg-gray-600 w-8 h-5 rounded-full'"
      class="relative inline-flex flex-shrink-0 h-[38px] w-[74px] border-2 border-transparent rounded-full cursor-pointer transition-colors ease-in-out duration-200 focus:outline-none focus-visible:ring-2 focus-visible:ring-white focus-visible:ring-opacity-75"
    >
      <span class="sr-only"></span>
      <span
        aria-hidden="true"
        :class="enabled ? ' enable bg-green-400 translate-x-100' : 'bg-white translate-x-0'"
        class="toggle-checkbox absolute block  h-4 w-4 rounded-full"
      />
    </Switch>
  </div>
</template>

<script>
import { ref } from 'vue'
import { Switch } from '@headlessui/vue'

export default {
  components: { Switch },

  setup() {
    const enabled = ref(false)
    return { enabled }
  },
}
</script>

<style scoped>
.enable {
  transform: translateX(90%);
  background-color: #48bb78;
}
</style>
