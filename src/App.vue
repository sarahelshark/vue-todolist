<script>
export default {
  name: "App",
  data() {
    return {
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
  },
};
</script>

<template>
  <div class="card p-6 shadow">
    <h1 class>to do list</h1>

    <div class="input-group mb-3">
       <input type="text">
       <button class="btn btn-dark">add</button>
    </div>
    
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
      
      --></li>
    </ul>
    <p v-else>niente da fare, buon relax! :D</p>
  </div>
</template>

<style></style>
