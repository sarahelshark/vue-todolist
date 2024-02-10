<script>
export default {
  name: "App",
  data() {
    return {
      tasks: [
        {
          text: "learn HTML",
          done: true,

        },
        {
          text: "learn JS",
          done: true,

        },
        {
          text: "learn Vue",
          done: false,

        },
      ],
      newTask: "",
      error: false,
      fullList: false,
    }

  },
  methods: {
    deleteTask(i) {
      this.tasks.splice(i, 1);
      if (this.tasks.length === 0) {
        this.fullList = false;
      };
      let itemList = []
      this.tasks.forEach((task, index) => {
        if (task.done === false) {
          itemList.push(index);
        };
        if (itemList === "") {
          this.fullList = true;
        } else { this.fullList = false };
        console.log(itemList);
      });
    },
    addTask() {
      if (this.newTask != "" && this.newTask.length>5) {
        const newTaskEl = { text: this.newTask, done: false, };
        let included;
        this.tasks.forEach(task => {
          if (task.text == newTaskEl.text) {
            included = true;
          };
        });
        if (!included) {
          this.error = false;
          this.tasks.push(newTaskEl);
          this.newTask = "";
          this.fullList = false;
          console.log(this.tasks);
        } else { this.error = "il tuo task risulta inserito" };

      }else { this.error = "non puoi lasciare vuoto! aggiungi almeno 5 caratteri!" }
      
    },
    allDone(i) {
      if (this.tasks[i].done == true) {
        this.tasks[i].done = false;
      } else { this.tasks[i].done = true };
      let count = 0;
      this.tasks.forEach(task => {
        if (task.done == true) {
          count += 1;
        };
      });

      if (count == this.tasks.length) {
        this.fullList = true;
      } else { this.fullList = false };
      console.log(count);
      console.log(this.tasks.length);
    },
    emptyList() {
      this.tasks = [];
      this.fullList = false;
    }
  }
}
</script>

<template>
  <div class="container text-center my-5">
    <h1 class="text-dark">Todo List</h1>
    <div class="input-group mb-3 ms-auto">
      <input class="form-control" v-model="newTask" @keyup.enter="addTask" type="text" name="newTask" id="newTask"
        placeholder="Insert your new Task">
      <button class="btn btn-outline-dark" @click="addTask">Add</button>
    </div>

    <p class="text-danger" v-if="error">{{ error }}</p>

    <ul class="list-group">
      <li class="list-group-item d-flex" v-for="( task, index ) in  tasks ">
        <input class="check form-check-input me-3" type="checkbox" v-model="task.done" @click="allDone(index)">
        <div style="width: 100%;" class="d-flex justify-content-between align.items-center">
          <div class="task" :class="{ done: task.done }" @click="allDone(index)">{{ task.text
          }}</div>
          <div class="delete" @click="deleteTask(index)"> x</div>
        </div>
      </li>
    </ul>
    <button v-if="fullList" class="btn btn-primary mt-5" @click="emptyList">Empty the list</button>
    <h3 v-if="tasks == ''">You have nothing else to do!</h3>
  </div>
</template>

<style>
/*#region reset */


/* #endregion */

.done {
  text-decoration: line-through;
}

.delete:hover {
  color: #dc3545;
}

.check,
.task,
.delete {
  cursor: pointer;
}
</style>