<template>
  <div class="todo-view">
    <h1>The Best Todo App</h1>
    <button @click="onButtonClicked" class="load-button">Load todos</button>
    <p>
      <label for="new-todo">Add new todo:</label>
      <input type="text" id="new-todo" />
    </p>
    <p>
      <button @clicked="onButtonClicked" class="add-button">Add</button>
    </p>
    <ul class="item-list">
      <li class="item-card">
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

<style scoped>
button {
  background-color: rgb(170, 218, 170);
  /* padding: 10px; */
  border-radius: 5px;
}

.load-button {
  height: 40px;
  width: 100px;
}

.add-button {
  height: 25px;
  width: 80px;
}

input:focus {
  background: lightblue;
}

input[type="text"] {
  border-radius: 5px;
  margin-left: 20px;
  padding: 3px;
}

.item-list {
  list-style: none;
  padding: none;
}
</style>
