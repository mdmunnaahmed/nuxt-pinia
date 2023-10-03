<template>
  <form @submit.prevent="formSubmit">
    <input type="text" placeholder="I need to. . ." v-model="newTask" />
    <button>Add Task</button>
  </form>
</template>

<script>
import { ref } from "vue";
import { useTaskStore } from "~/stores/TaskStore";
export default {
  setup() {
    const taskStore = useTaskStore();
    const newTask = ref("");
    const formSubmit = () => {
      if (newTask.value.length > 0) {
        taskStore.addTask({
          title: newTask.value,
          isFav: false,
          id: Math.floor(Math.random() * 10000),
        });
        newTask.value = "";
      }
    };
    return { formSubmit, newTask };
  },
};
</script>