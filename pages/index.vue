<template>
  <main>
    <!-- heading -->
    <header>
      <img src="https://pinia.vuejs.org/logo.svg" alt="pinia logo" />
      <h1>Nuxt Store</h1>
      <h1>{{ taskStore.name }}</h1>
    </header>

    <div class="new-task-form">
      <TaskForm />
    </div>

    <nav class="filter">
      <button @click="filter = 'all'">All Tasks</button>
      <button @click="filter = 'favs'">Fav Tasks</button>
    </nav>

    <div class="loading" v-if="isLoading">Loading tasks...</div>

    <div class="task-list" v-if="filter === 'all'">
      <p>You have Total ({{ totalCount }}) to do</p>
      <div v-for="task in tasks" :key="task">
        <TaskDetails :task="task" />
      </div>
    </div>

    <div class="task-list" v-if="filter === 'favs'">
      <p>Favs Tasks ({{ favCount }})</p>
      <div v-for="task in favs" :key="task">
        <TaskDetails :task="task" />
      </div>
    </div>

    <div class="" style="text-align: center">
      <button @click="taskStore.$reset">Reset</button>
    </div>
  </main>
</template>

<script>
import { useTaskStore } from '~/stores/TaskStore';
export default {
  setup() {
    const taskStore = useTaskStore();

    taskStore.getTasks();

    // const filter = ref("all");
    return { taskStore };
  },
};
</script>