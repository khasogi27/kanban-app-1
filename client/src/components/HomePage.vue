<template>
<div>

<!--Navbar -->
<nav class="mb-1 navbar navbar-expand-lg navbar-dark orange lighten-1">
  <div class="collapse navbar-collapse" id="navbarSupportedContent-555">
    <ul class="navbar-nav mr-auto">
      <li class="nav-item1 active mr-2">
        <a class="nav-link" href="" @click.prevent="toAdd">New Task
        </a>
      </li>
      <li class="nav-item2 active mr-2">
        <a class="nav-link" href="" @click.prevent="logout">Logout
        </a>
      </li>
    </ul>
  </div>
</nav>
<!--/.Navbar -->
  <div class="container-fluid pt-3">
    <h3 class="font-weight-light text-white fab fa-10x">Kanban Board</h3>
    <div class="row flex-row flex-sm-nowrap py-3">
    <Category
    v-for="(cat, i) in categories"
    :key = "i"
    :categor="cat"
    @kirimTaskUntukEdit="kirimDataTaskUntukEdit"
    @editCategory="editCategory"
    @deleteTasks="deleteTasks"
    ></Category>
    </div>
  </div>
</template>

<script>
import Category from "./Category";
export default {
  name: "HomePage",
  components: {
    Category,
  },
  props: ["task", "categories"],
  methods: {
    kirimDataTaskUntukEdit(tasks) {
      this.$emit("kirimTaskUntukEdit", tasks);
    },

    editCategory(id) {
      this.$emit("moveCategory", id);
    },

    deleteTasks(id) {
      this.$emit("deleteTasks", id);
    },

    logout() {
      console.log("logout yah");
      localStorage.clear();
      this.$emit("changePage", "login-page");
    },

    toAdd() {
      this.$emit("changePage", "add-page");
    },
  },
};
</script>

<style>
</style>