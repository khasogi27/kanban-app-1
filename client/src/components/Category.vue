<template>
  <div class="col-sm-6 col-md-4 col-xl-3 mt-3">
    <div class="card bg-light">
      <div class="card-body">
        <h3 class="card-title text-uppercase text-truncate py-2">
          {{ categor.name }}
        </h3>
        <div class="items border border-light">
          <Description
            v-for="(task, i) in categor.Tasks"
            :key="i"
            :tasks="task"
            :categor="categor"
            @kirimTaskUntukEdit="kirimDataTaskUntukEdit"
            @editCategory="editCategory"
            @deleteTasks="deleteTasks"
          ></Description>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Description from "./Description";
export default {
  name: "Category",
  components: {
    Description,
  },
  props: ["categor"],
  methods: {
    kirimDataTaskUntukEdit(tasks) {
      this.$emit("kirimTaskUntukEdit", tasks);
    },

    editCategory(id) {
      this.$emit("editCategory", id);
    },

    deleteTasks(id) {
      this.$emit("deleteTasks", id);
    },
  },
};
</script>

<style>
</style>