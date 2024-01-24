<script>

export default {
  name: "App",
  data() {
    return {
      toDoList: [
        {
          text: "Pagare Bollette",
          done: true,
        },
        {
          text: "Portare fuori il cane",
          done: false,
        },
        {
          text: "Preparare il pranzo",
          done: false,
        },
        {
          text: "Rifare il letto",
          done: false,
        },
        {
          text: "Fare l'esercizio",
          done: false,
        },
        {
          text: "Fare la spesa",
          done: false,
        },
      ],

    }
  },
  methods: {
    remove(index) {
      this.toDoList[index].done = true;
    }
  }
}

</script>

<template>
  <div class="container">
    <h1>To Do List</h1>
    <ul>
      <li v-for="(item, index) in toDoList" :class="item.done ? 'line-through' : ''">
        {{ item.text }}
        <span>
          <i class="fa-solid fa-square-xmark" @click="remove(index)"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<style ></style>
