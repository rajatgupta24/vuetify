<template>
  <Header msg="Todo APP"></Header>
  <Form @add-task="addTask"></Form>
  <List @delete-task="deleteTask" :tasks="tasks"></List>
</template>

<script>
import Header from "./components/Header.vue"
import Form from "./components/Form.vue"
import List from "./components/List.vue"

export default {
  name: 'App',
  data() {
    return {
      tasks: []
    }
  },
  components: {
    Header,
    Form,
    List,
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      console.log(id)
      this.tasks = this.tasks.filter((task) => task.id !== id)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        task: "Task 1",
        des: "This is task 1",
        category: "work",
        completed: false

      },
      {
        id: 2,
        task: "Task 2",
        des: "This is task 2.",
        category: "home",
        completed: false

      },
      {
        id: 3,
        task: "Task 3",
        des: "This is task 3",
        category: "work",
        completed: false

      },
    ]
  }
}
</script>

<style></style>
