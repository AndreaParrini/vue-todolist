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
      toDoCancelled: [],
    }
  },
  methods: {
    remove(item, index) {
      this.toDoList.splice(index, 1);
      this.toDoCancelled.push(item);
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

    },
    deleteCancelled(item, index) {
      this.toDoCancelled.splice(index, 1);
      this.toDoList.push(item);
    }
  }
}

</script>

<template>
  <div class="container">
    <div class="card justify-content-center mt-3">
      <h1>To Do List</h1>
      <div class="input-group input-group-md mb-3 justify-content-center">
        <input type="text" v-model="newItem" @keyup.enter="addItem(newItem)">
        <button class=" btn btn-dark" @click="addItem(newItem)">
          Aggiungi
        </button>
      </div>
      <div v-if="errorMessage" class="text-center">
        <span class="text-danger fs-5">
          <i class="fa-solid fa-triangle-exclamation"></i>
          Devi inserire almeno 5 caratteri
          <i class="fa-solid fa-triangle-exclamation"></i>
        </span>
      </div>

      <div class="card-body m-auto w-75">
        <ul v-if="toDoList.length > 0" class="list-group">
          <li v-for="( item, index ) in    toDoList   "
            class="list-group-item d-flex justify-content-between fs-5 border border-black">
            <span :class="{ 'line-through': item.done }" @click="item.done = !item.done">{{ item.text
            }}</span>
            <span>
              <i class="fa-solid fa-square-xmark" @click="remove(item, index)"></i>
            </span>
          </li>
        </ul>
        <p v-else class="text-center fs-5">
          <i class="fa-solid fa-face-grin-beam"></i>
          Complimenti, hai completato tutte le tue cose da fare.
          Goditi la giornata.
          <i class="fa-solid fa-sun"></i>
        </p>
      </div>

    </div>

    <div class="card justify-content-center mt-3">
      <h1>To Do Cancelled</h1>

      <div class="card-body m-auto w-75">
        <ul v-if="toDoCancelled.length > 0" class="list-group">
          <li v-for="(item, index) in toDoCancelled   "
            class="list-group-item d-flex justify-content-between fs-5 border border-danger">
            <span class="text-danger">{{ item.text
            }}</span>
            <span>
              <i class="fa-solid fa-trash-can-arrow-up" @click="deleteCancelled(item, index)"></i>
            </span>
          </li>
        </ul>
        <p v-else class="text-center fs-5">
          <i class="fa-solid fa-face-grin-beam"></i>
          Non hai nessuna To Do cancellata!
          <i class="fa-solid fa-face-grin-beam"></i>
        </p>
      </div>

    </div>

  </div>
</template>

<style ></style>
