<template>
  <div class="task">
    <h3>{{ task.title }}</h3>
    <div class="icons flex gap-2">
      <span class="material-icons" @click="taskStore.deleteTask(task.id)"
        ><svg
          viewBox="0 0 24 24"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
          width="20"
        >
          <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
          <g
            id="SVGRepo_tracerCarrier"
            stroke-linecap="round"
            stroke-linejoin="round"
          ></g>
          <g id="SVGRepo_iconCarrier">
            <path
              d="M9.1709 4C9.58273 2.83481 10.694 2 12.0002 2C13.3064 2 14.4177 2.83481 14.8295 4"
              stroke="#1C274C"
              stroke-width="1.5"
              stroke-linecap="round"
            ></path>
            <path
              d="M20.5001 6H3.5"
              stroke="#1C274C"
              stroke-width="1.5"
              stroke-linecap="round"
            ></path>
            <path
              d="M18.8332 8.5L18.3732 15.3991C18.1962 18.054 18.1077 19.3815 17.2427 20.1907C16.3777 21 15.0473 21 12.3865 21H11.6132C8.95235 21 7.62195 21 6.75694 20.1907C5.89194 19.3815 5.80344 18.054 5.62644 15.3991L5.1665 8.5"
              stroke="#1C274C"
              stroke-width="1.5"
              stroke-linecap="round"
            ></path>
            <path
              d="M9.5 11L10 16"
              stroke="#1C274C"
              stroke-width="1.5"
              stroke-linecap="round"
            ></path>
            <path
              d="M14.5 11L14 16"
              stroke="#1C274C"
              stroke-width="1.5"
              stroke-linecap="round"
            ></path>
          </g></svg
      ></span>
      <span
        class="material-icons"
        :class="{ active: task.isFav }"
        @click="taskStore.toggleFav(task.id)"
        ><svg width="20" fill="#666" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"><path d="M20.5,4.609A5.811,5.811,0,0,0,16,2.5a5.75,5.75,0,0,0-4,1.455A5.75,5.75,0,0,0,8,2.5,5.811,5.811,0,0,0,3.5,4.609c-.953,1.156-1.95,3.249-1.289,6.66,1.055,5.447,8.966,9.917,9.3,10.1a1,1,0,0,0,.974,0c.336-.187,8.247-4.657,9.3-10.1C22.45,7.858,21.453,5.765,20.5,4.609Zm-.674,6.28C19.08,14.74,13.658,18.322,12,19.34c-2.336-1.41-7.142-4.95-7.821-8.451-.513-2.646.189-4.183.869-5.007A3.819,3.819,0,0,1,8,4.5a3.493,3.493,0,0,1,3.115,1.469,1.005,1.005,0,0,0,1.76.011A3.489,3.489,0,0,1,16,4.5a3.819,3.819,0,0,1,2.959,1.382C19.637,6.706,20.339,8.243,19.826,10.889Z"></path></g></svg></span
      >
    </div>
  </div>
</template>

<script>
import { useTaskStore } from "~/stores/TaskStore";
export default {
  props: ["task"],
  setup() {
    const taskStore = useTaskStore();
    return { taskStore };
  },
};
</script>