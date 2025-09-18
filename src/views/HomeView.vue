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
        <p v-for="item in data" :key="item.id">
          <span>{{ item.id }}</span>
          <span>
            <s v-if="item.completed">{{ item.title }}</s>
            <span v-else>{{ item.title }}</span>
          </span>
          <span>
            <label>
              done?
              <input type="checkbox" v-model="item.completed" />
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

<script>
export default {
  name: "home-view",

  data() {
    return {
      data: [{ id: -1, title: "none", completed: false }], // same default
    };
  },

  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos")
      .then((response) => response.json())
      .then((response) => response.splice(0, 50)) // just limiting to 50
      .then((json) => console.log(json));
  },

  methods: {
    onButtonClicked() {
      alert("MethodNotImplementedException");
    },
  },
};
</script>
