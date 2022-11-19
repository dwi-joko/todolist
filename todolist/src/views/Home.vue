<template>
  <main>
    <div class="container">
      <div class="header-content">
        <h2>Activity</h2>
        <a class="btn-default" data-bs-toggle="modal" data-bs-target="#exampleModal">
          <div class="icon">+</div>
          <p>Tambah</p>
        </a>
      </div>
      <div class="content todo-list">
        <!-- <h1>{{ info }}</h1> -->
        <!-- <table class="table" v-if="todos">
          <thead>
            <tr>
              <th>Checklist</th>
              <th>Items</th>
              <th>CTA</th>
            </tr>
          </thead>
          <tbody v-for="(todo, index) in todos" :key="index">
            <td>{{ todo.content }}</td>
            <td>{{ todo }}</td>
            <td><a href="#" @click="removeTodo(index)" class="btn-icon">Delete</a></td>
          </tbody>
        </table> -->
        <div class="todos">
          <h1>{{ info }}</h1>
        </div>

        <div class="images">
          <img src="@/assets/activity-empty-state.png" alt="" />
          <h3>kosong mas</h3>
        </div>
      </div>
    </div>

    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h1 class="modal-title fs-5" id="exampleModalLabel">Tambah List Item</h1>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
            <form @submit.prevent="addTodo()" action="create">
              <div class="mb-3">
                <label for="exampleFormControlInput1" class="form-label">NAMA LIST ITEM</label>
                <input type="text" class="form-control" id="todo" v-model="newTodo" @keyup.enter="newTodo" name="newTodo" placeholder="Tambahkan nama list item" />
              </div>
              <div class="mb-3">
                <label for="exampleFormControlInput1" class="form-label">Priority</label>
                <select class="form-select" aria-label="Default select example">
                  <option selected>Open this select menu</option>
                  <option value="1">One</option>
                  <option value="2">Two</option>
                  <option value="3">Three</option>
                </select>
              </div>
            </form>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <button type="button" @click="addTodo()" class="btn btn-primary">Save changes</button>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
// import { ref } from "vue";
export default {
  name: "Home",
  components: {},
  // methods: {
  //   addTodo() {
  //     this.todos.push(this.todo);
  //     this.todo = "";
  //   },
  //   deleteTodo(index) {
  //     this.todo.splice(index, 1);
  //   },
  // },
  // watch: {
  //   todos() {
  //     localStorage.setItem("todos", JSON.stringfy(this.todos));
  //   },
  // },
  // methods: {
  //   getList() {
  //     this.axios.get(api).then((response) => {
  //       console.log(response.data)
  //     })
  //     // or
  //     this.$http.get(api).then((response) => {
  //       console.log(response.data)
  //     })
  //   }
  // }
  mounted() {
    axios
      .get("https://www.postman.com/collections/b0a48bb59c1511914c46")
      .then((response) => (this.info = response))
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  },

  // setup() {
  //   const newTodo = ref("");
  //   const defaultData = [
  //     {
  //       done: false,
  //       content: "Write a blog post",
  //     },
  //   ];
  //   const todosData = JSON.parse(localStorage.getItem("todos")) || defaultData;
  //   const todos = ref(todosData);
  //   function addTodo() {
  //     if (newTodo.value) {
  //       todos.value.push({
  //         done: false,
  //         content: newTodo.value,
  //       });
  //       newTodo.value = "";
  //     }
  //     saveData();
  //   }
  //   function doneTodo(todo) {
  //     todo.done = !todo.done;
  //     saveData();
  //   }
  //   function removeTodo(index) {
  //     todos.value.splice(index, 1);
  //     saveData();
  //   }
  //   function saveData() {
  //     const storageData = JSON.stringify(todos.value);
  //     localStorage.setItem("todos", storageData);
  //   }
  //   return {
  //     todos,
  //     newTodo,
  //     addTodo,
  //     doneTodo,
  //     removeTodo,
  //     saveData,
  //   };
  // },
};
</script>
