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
  <h1 >to do list</h1>

  <ul>
    <li v-for="task in tasks">
      <span :style="{textDecoration: task.done ? 'line-through': ''}">  {{ task.text }}
      </span>  
      <!--con style binding posso far passare oggetto, altrimnenti potrei impotare bootstrap e usare il class binding v-bind:class="{}",sarebbe stato:

        <span v-bind:class="{'text-decoration-line-through' : task.done}"> 
           {{ task.text }}
        </span>      text-decoration-line-through> la classe di bs5
      
      --> 
    </li>
  </ul>

</template>

<style>



</style>
