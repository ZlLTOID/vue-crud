// If style is scoped styles will apply on current component
<style scoped>

</style>

<script setup>
import { onMounted, ref } from 'vue';

      const name = ref('John Doe');
      const status = ref('active');
      // const tasks = ref(['Task one', 'Task two', 'Task three']);
      const tasks = ref({});
      const newTask = ref('');

      onMounted(async () => {
        try {
          const response = await fetch('https://jsonplaceholder.typicode.com/todos');
          const data = await response.json();
          console.log(data);
          tasks.value = data.map((task) => task.title)
        } catch (error) {
          console.log('Error fetching tasks');
        }
      });

      function toggleStatus() {
        if (status.value === 'active') {
          status.value = 'pending';
          console.log(status);
        } else {
          status.value = 'active';
        }
      }

      function addTask() {
        if (newTask.value !== '') {
          console.log(newTask.value);
          tasks.value.push(newTask.value);
          newTask.value = '';
        }
      }

      function deleteTask(taskToDelete) {
        tasks.value.splice(taskToDelete, 1);
      }

</script>


<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>
  
  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks">
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>
  <a :href=link>Link to Google.com</a>
  <br>
  <br>
  <button @click=toggleStatus>Change status</button>
  <form @submit.prevent="addTask" class="row">
              <input type="text" id="input-box" name="newTask" v-model="newTask">
              <button type="submit">Add</button>
          </form>
</template>
