<script>
export default {
  name: "App",
  data() {
    return {
      tasks: [
        {
          text:"Learn HTML",
          done: true,
        }
        ,
        {
          text:"Learn CSS",
          done: true,
        }
        ,
        {
          text:"Learn VUE",
          done: false,
        },
      ],
    };
  },
};
</script>

<template>
  <h1>to do list</h1>

  <ul>
    <li v-for="task in tasks">
      <span :style="{textDecoration: task.done ? 'line-through': ''}">  {{ task.text }}
      </span>  <!--con style binding posso far passare oggetto -->
    </li>
  </ul>

</template>

<style>



</style>
