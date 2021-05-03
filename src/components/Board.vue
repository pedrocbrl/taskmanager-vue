<template>
  <div class="col-md-3">
    <div class="row">
      <div class="col">
        <b-form-input
          v-model="newTask"
          placeholder="Enter task"
          @keyup.enter="add"
        ></b-form-input>
      </div>
      <div class="align-self-end">
          <b-button class="mr-3" variant="primary" @click="add"
          >Add Task</b-button
        >
      </div>
    </div>
    <div :class="classData">
      <h3>{{ title }}</h3>
      <draggable
        class="list-group draggable-container task"
        :list="tasksArray"
        group="tasks"
      >
        <div
          class="list-group-item"
          v-for="element in tasksArray"
          :key="element.name"
        >
          {{ element.name }}
        </div>
      </draggable>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
export default {
  name: "Board",
  props: {
    title: { type: String, default: "New Task" },
    classData: { type: String, default: "p-2 alert green" },
  },
  components: {
    draggable,
  },
  data() {
    return {
      newTask: "",
      tasksArray: [],
    };
  },
  methods: {
    add() {
      if (this.newTask) {
        this.tasksArray.push({ name: this.newTask });
        this.newTask = "";
      }
    },
  },
};
</script>

<style>
/* 
  To change mouse cursor while dragging
  https://github.com/SortableJS/Vue.Draggable/issues/815
*/
.green {
  background-color: #23be97;
  color: #fff;
}
.yellow {
  background-color: #d5c36e;
  color: #fff;
}
.orange {
  background-color: #c37e44;
  color: #fff;
}
.red {
  background-color: #b5414a;
  color: #fff;
}
.blue {
  background-color: #84baec;
  color: #fff;
}
.draggable-container {
  min-height: 300px;
}
.task {
  color: #212529;
}
</style>