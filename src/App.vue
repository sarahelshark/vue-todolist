<script>
export default {
  name: "App",
  data() {
    return {
      newTask: {
          text: '',
          done: false
        },
      error: false, //oppure null
      tasks: [
        {
          text: "Learn HTML",
          done: true,
        },
        {
          text: "Learn CSS",
          done: true,
        },
        {
          text: "Learn VUE",
          done: false,
        },
      ],
    };
  },
  methods: {
    removeTask(index) {
      console.log("rimuovi questa task", index);
      this.tasks.splice(index, 1);
      //.splice mi serve perrimovere un elemento dal suo indice
    },
    addTask() {
      console.log("aggiungi nuova task ad array di tasks", this.newTask);

      if (this.newTask.length > 5) {
        this.error = false;
        this.tasks.unshift(this.newTask);
        this.newTask = "";
      } else {
        this.error = "la task deve essere lunga min 5 caratteri";
      }
    },
  },
};
</script>

<template>
  <div class="card p-6 shadow">
    <h1 class>to do list</h1>

    <div class="input-group mb-3">
      <input type="text" v-model="newTask.text" @keyup.enter="addTask" />
      <button class="btn btn-dark" @click="addTask">add</button>
    </div>
    <span class="text-danger" v-if="error">{{ error }}</span>
    <div class="ul list-group">
      <ul v-if="tasks.length > 0">
        <li v-for="(task, index) in tasks">
          <span :style="{ textDecoration: task.done ? 'line-through' : '' }">
            {{ task.text }}

            <span v-on:click="removeTask(index)">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="16"
                height="16"
                fill="currentColor"
                class="bi bi-x-circle"
                viewBox="0 0 16 16"
              >
                <path
                  d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14m0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16"
                />
                <path
                  d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708"
                />
              </svg>
            </span>
          </span>
          <!--con style binding posso far passare oggetto, altrimnenti potrei impotare bootstrap e usare il class binding v-bind:class="{}",sarebbe stato:

        <span v-bind:class="{'text-decoration-line-through' : task.done}"> 
           {{ task.text }}
        </span>      text-decoration-line-through> la classe di bs5
      
      -->
        </li>
      </ul>
      <p v-else>niente da fare, buon relax! :D</p>
    </div>
  </div>
</template>

<style></style>
