<template>
  <div class="conatiner mt-5 ml-3 mr-3">
    <div class="row mt-3">
      <board title="Open" classData="p-2 alert blue"></board>
      <board title="In Progress" classData="p-2 alert yellow"></board>
      <board title="Done" classData="p-2 alert green"></board>
    </div>
  </div>
</template>

<script>
import Board from "./components/Board.vue";

document.title = "Task Manager";

export default {
  name: "App",
  components: {
    Board,
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
