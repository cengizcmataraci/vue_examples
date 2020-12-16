<template>
  <div id="practice" class="col d-flex justify-content-center ust">
    <todoList />
    <counter />
  </div>
</template>

<script>
import TodoList from "./components/TodoList";
import Counter from "./components/Counter";

export default {
  name: "practice",
  components: {
    todoList: TodoList,
    counter: Counter,
  },
};
</script>

<style>
.ust {
  margin-top: 150px;
  text-align: center;
  vertical-align: middle;
}
.dangertext {
  color: #f9000f;
  font-size: larger;
}
.dangerZone {
  background-color: darkred;
  color: aliceblue;
}
</style>
