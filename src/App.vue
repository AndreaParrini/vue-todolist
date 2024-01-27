<script>

export default {
  name: "App",
  data() {
    return {
      newItem: '',
      errorMessage: false,
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
    },
    addItem(newItem) {
      if (newItem.length > 4) {
        this.errorMessage = false;
        this.toDoList.push({
          text: newItem,
          done: false
        });
        this.newItem = "";
      } else {
        this.errorMessage = true;
      }

    }
  }
}

</script>

<template>
  <div class="container">
    <h1>To Do List</h1>
    <div>
      <input type="text" v-model="newItem" @keyup.enter="addItem(newItem)">
      <button class=" btn button" @click="addItem(newItem)">
        Aggiungi
      </button>
    </div>
    <div v-if="errorMessage">
      <span class="text-danger">
        <i class="fa-solid fa-triangle-exclamation"></i>
        Devi inserire ameno 5 caratteri
        <i class="fa-solid fa-triangle-exclamation"></i>
      </span>
    </div>
    <ul v-if="toDoList.length > 0">
      <li v-for="( item, index ) in    toDoList   ">
        <span :class="{ 'line-through': item.done }">{{ item.text }}</span>
        <span>
          <i class="fa-solid fa-square-xmark" @click="remove(index)"></i>
        </span>
      </li>
    </ul>

    <p v-else>Niente da fare, goditi la giornata</p>
  </div>
</template>

<style ></style>
