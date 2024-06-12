<template>
  <div class="container">
    <h1>My To Do List</h1>
    <input v-model="newTask" placeholder="Add a new task" />
    <button @click="addTask">Add</button>

    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <button @click="editTask(index)">Edit</button>
        <button @click="deleteTask(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [],
      newTask: "",
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== "") {
        this.tasks.push(this.newTask);
        this.newTask = "";
      }
    },
    editTask(index) {
      const updatedTask = prompt("Update the task", this.tasks[index]);
      if (updatedTask && updatedTask.trim() !== "") {
        this.tasks.splice(index, 1, updatedTask);
      }
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style scoped>

h1 {
  text-align: center;
  font-size: 24px;
  color: #333;
  margin-bottom: 20px;
}

input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 10px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 5px;
  background: linear-gradient(135deg, #f6d365 0%, #fda085 100%);
  padding: 10px;
  border-radius: 4px;

}

button {
  padding: 5px 10px;
  font-size: 14px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  background-color: #333;
  color: #fff;
}

button:hover {
  background-color: #555;
}

</style>
