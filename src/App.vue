<template>
  <div class="conatiner mt-5 ml-3 mr-3">
    <div class="row">
      <div class="col form-inline">
        <b-form-input
          v-model="newTask"
          placeholder="Enter task"
          @keyup.enter="add"
        ></b-form-input>
        <b-button class="ml-2" variant="primary" @click="add"
          >Add Task</b-button
        >
      </div>
    </div>

    <div class="row mt-3">
      <div class="col-md-3">
        <div class="p-2 alert backlog">
          <h3>BackLog</h3>
          <draggable
            class="list-group draggable-container task"
            :list="arrBackLog"
            group="tasks"
          >
            <div
              class="list-group-item"
              v-for="element in arrBackLog"
              :key="element.name"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert in-progress">
          <h3>In Progress</h3>
          <draggable
            class="list-group draggable-container task"
            :list="arrInProgress"
            group="tasks"
          >
            <div
              class="list-group-item"
              v-for="element in arrInProgress"
              :key="element.name"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert tested">
          <h3>Tested</h3>
          <draggable
            class="list-group draggable-container task"
            :list="arrTested"
            group="tasks"
          >
            <div
              class="list-group-item"
              v-for="element in arrTested"
              :key="element.name"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert done">
          <h3>Done</h3>
          <draggable
            class="list-group draggable-container task"
            :list="arrDone"
            group="tasks"
          >
            <div
              class="list-group-item"
              v-for="element in arrDone"
              :key="element.name"
            >
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";

document.title = "Task Manager";

export default {
  name: "App",
  components: {
    draggable,
  },
  data() {
    return {
      newTask: "",
      arrBackLog: [
        { name: "Code Sign Up Page" },
        { name: "Test Dashboard" },
        { name: "Style Registration" },
        { name: "Help with Designs" },
      ],
      arrInProgress: [],
      arrTested: [],
      arrDone: [],
    };
  },
  methods: {
    add() {
      if (this.newTask) {
        this.arrBackLog.push({ name: this.newTask });
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
.backlog {
  background-color: #23be97;
  color: #fff;
}
.in-progress {
  background-color: #d5c36e;
  color: #fff;
}
.tested {
  background-color: #c37e44;
  color: #fff;
}
.done {
  background-color: #b5414a;
  color: #fff;
}
.draggable-container {
  min-height: 300px;
}
.task {
  color: #212529;
}
</style>
