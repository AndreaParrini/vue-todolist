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
          done: true,
        },
        {
          text: "Fare l'esercizio",
          done: false,
        },
        {
          text: "Fare la spesa",
          done: true,
        },
      ],

    }
  },
  methods: {
    remove(index) {
      this.toDoList.splice(index, 1)
      /* if (this.toDoList[index].done) {
        this.toDoList[index].done = false;
      } else {
        this.toDoList[index].done = true;
      } */
    }
  }
}

</script>

<template>
  <div class="container">
    <h1>To Do List</h1>
    <ul>
      <li v-for="(item, index) in toDoList">
        <span :class="item.done ? 'line-through' : ''">{{ item.text }}</span>
        <span>
          <i class="fa-solid fa-square-xmark" @click="remove(index)"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<style ></style>
