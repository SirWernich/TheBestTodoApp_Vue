<template>
  <div class="home">
    <h1>The Best Todo App</h1>
    <button @click="onButtonClicked">Load todos</button>
    <p>
      <label for="new-todo">Add new todo:</label>
      <input type="text" id="new-todo" />
      <button @clicked="onButtonClicked">Add</button>
    </p>
    <ul>
      <li>
        <p>
          <span>{{ data[0].id }}</span>
          <span>
            <s>{{ data[0].title }}</s>
          </span>
          <span>
            <label>
              done?
              <input
                type="checkbox"
                :value="data[0].completed ? 'checked' : ''"
              />
            </label>
          </span>
        </p>
      </li>
    </ul>
  </div>
</template>

<style scoped>
button {
  background-color: fuchsia;
}

input {
  border: 2px dotted green;
}
</style>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({
  name: "home-view",
})
export default class HomeView extends Vue {
  private data: any = [{ id: -1, title: "none", completed: false }]; // gives error when array empty

  private mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos")
      .then((response) => response.json())
      .then((response) => response.splice(0, 50)) // just limiting it to 50
      .then((json) => console.log(json));
  }

  private onButtonClicked() {
    alert("MethodNotImplementedException");
  }
}
</script>
