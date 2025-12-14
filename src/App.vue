<script setup>
import { ref } from "vue";

// State menggunakan ref()
const tasks = ref([]);
const newTask = ref("");

// Fungsi untuk menambah tugas
const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value.trim());
    newTask.value = ""; // Reset input setelah menambah tugas
  }
};

// Fungsi untuk menghapus tugas
const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};
</script>

<template>
  <div class="todo-app">
    <h1>📝 To-Do List App</h1>

    <!-- Form untuk menambah tugas -->
    <form @submit.prevent="addTask" class="add-task-form">
      <input
        v-model="newTask"
        type="text"
        placeholder="Masukkan tugas baru..."
        class="task-input"
      />
      <button type="submit" class="add-btn">Tambah Tugas</button>
    </form>

    <!-- Daftar tugas -->
    <div class="tasks-container">
      <h2>Daftar Tugas</h2>

      <!-- Kondisi jika tidak ada tugas -->
      <p v-if="tasks.length === 0" class="no-tasks">Tidak ada tugas</p>

      <!-- List tugas menggunakan v-for -->
      <ul v-else class="tasks-list">
        <li v-for="(task, index) in tasks" :key="index" class="task-item">
          <span class="task-text">{{ task }}</span>
          <button @click="deleteTask(index)" class="delete-btn">
            🗑️ Hapus
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.todo-app {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  font-family: "Arial", sans-serif;
}

h1 {
  text-align: center;
  color: #2c3e50;
  margin-bottom: 30px;
}

.add-task-form {
  display: flex;
  gap: 10px;
  margin-bottom: 30px;
}

.task-input {
  flex: 1;
  padding: 12px;
  border: 2px solid #ddd;
  border-radius: 8px;
  font-size: 16px;
  outline: none;
  transition: border-color 0.3s;
}

.task-input:focus {
  border-color: #3498db;
}

.add-btn {
  padding: 12px 20px;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s;
}

.add-btn:hover {
  background-color: #2980b9;
}

.tasks-container {
  background-color: #f8f9fa;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

h2 {
  color: #2c3e50;
  margin-bottom: 15px;
}

.no-tasks {
  text-align: center;
  color: #7f8c8d;
  font-style: italic;
  padding: 20px;
}

.tasks-list {
  list-style: none;
  padding: 0;
}

.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  margin-bottom: 10px;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s;
}

.task-item:hover {
  transform: translateY(-2px);
}

.task-text {
  flex: 1;
  font-size: 16px;
  color: #2c3e50;
}

.delete-btn {
  padding: 8px 12px;
  background-color: #e74c3c;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 14px;
  transition: background-color 0.3s;
}

.delete-btn:hover {
  background-color: #c0392b;
}
</style>
