<template>
  <main>
    <!-- heading -->
    <header>
      <img src="https://pinia.vuejs.org/logo.svg" alt="pinia logo" />
      <h1>Nuxt Store</h1>
    </header>

    <div class="new-task-form">
      <TaskForm />
    </div>

    <nav class="filter">
      <button :class="{ active: (filter === 'all') }" @click="filter = 'all'">
        All Tasks
      </button>
      <button :class="{ active: (filter === 'favs') }" @click="filter = 'favs'">
        Fav Tasks
      </button>
    </nav>
    <div v-if="taskStore.loading" class="text-center bg-gray-300 container mx-auto mb-12 mt-10">
      <span>Loading</span>
    </div>

    <div class="task-list" v-if="filter === 'all'">
      <p>You have Total ({{ taskStore.totalCount }}) to do</p>
      <div v-for="task in taskStore.tasks" :key="task">
        <TaskDetails :task="task" />
      </div>
    </div>

    <div class="task-list" v-if="filter === 'favs'">
      <p>Favs Tasks ({{ taskStore.favCount }})</p>
      <div v-for="task in taskStore.favs" :key="task">
        <TaskDetails :task="task" />
      </div>
    </div>

    <div class="" style="text-align: center">
      <button @click="taskStore.$reset">Reset</button>
    </div>
  </main>
</template>

<script>
import { ref } from "vue";
import { useTaskStore } from "~/stores/TaskStore";
export default {
  setup() {
    const taskStore = useTaskStore();

    taskStore.getTasks();

    const filter = ref("all");
    return { taskStore, filter };
  },
};
</script>