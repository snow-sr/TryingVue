<template>
  <main>
    <div id="app" class="bg-slate-800 min-w-screen min-h-screen">
      <div class="bg-slate-600">
        <div class="max-w-7xl mx-auto py-12">
          <h1 class="text-5xl text-center text-purple-400">
            Lista de Afazeres
          </h1>
        </div>
      </div>

      <div class="flex justify-center my-5">
        <div class="mb-3 xl:w-96">
          <label @click="viewTasks" for="Tasks" class="form-label inline-block mb-2 text-white">
            Insira uma tarefa
          </label>
          <input
            type="text"
            class="
              form-control
              block
              w-full
              px-3
              py-1.5
              text-base
              font-normal
              text-gray-700
              bg-white bg-clip-padding
              border border-solid border-gray-300
              rounded
              transition
              ease-in-out
              m-0
              focus:text-gray-700
              focus:bg-white
              focus:border-blue-600
              focus:outline-none
            "
            v-model="input"
            placeholder="Ex: Levar o cachorro passear :)"
            required
          />
          <div class="flex space-x-2 my-3 justify-center">
            <button
              type="submit"
              id="addBtn"
              class="
                inline-block
                px-6
                py-2.5
                bg-purple-700
                text-white
                font-medium
                text-xs
                leading-tight
                uppercase
                rounded
                shadow-md
                hover:bg-purple-900 hover:shadow-lg
                focus:bg-blue-700
                focus:shadow-lg
                focus:outline-none
                focus:ring-0
                active:bg-blue-800 active:shadow-lg
                transition
                duration-150
                ease-in-out
              "
              @click="addTask"
            >
              Adicionar nova tarefa
            </button>
          </div>
        </div>
      </div>

      <div class="flex justify-center my-24 min-w-screen min-h-fit">
        <div
          class="
            min-w-screen
            h-7xl
            min-h-fit
            justify-center
            content-center
            flex
          "
        >
          <ul class="text-white list-disc justify-center">
            <li v-for="item in list" @click="() => {item.solved = true; removeSolvedTasks()}" class="hover:text-red-500">
              {{item.task}}
            </li>
          </ul>
       
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import { ref } from "vue";

const list = ref([]);
const input = ref("");

const addTask = () => {
  list.value.push({task: input.value, solved: false});
  input.value = "";
};

const removeSolvedTasks = () => {
  list.value = list.value.filter((item) => !item.solved);
};


const viewTasks = () => {
  console.log(list.value);
}


export default {
  data() {
    return {
      input,
      list,
    }
  },
  methods: {
    addTask,
    viewTasks,
    removeSolvedTasks
  },
};
</script>
