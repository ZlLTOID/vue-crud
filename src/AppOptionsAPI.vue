// If style is scoped styles will apply on current component
<style scoped>

</style>

<script>
  export default {
    data() {
      return {
        name: 'John Doe',
        status: 'pending',
        tasks: ['Task one', 'Task two', 'Task Three'],
        link: "https://google.com",
      }
    },
    methods: {
      toggleStatus() {
        if (this.status === 'active') {
          this.status = 'pending';
        } else {
          this.status = 'active';
        }
      }
    }
  }
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>
  
  <h3>Taksks:</h3>
  <ul>
    <li v-for="task in tasks">{{ task }}</li>
    <li></li>
  </ul>
  <a :href=link>Link to Google.com</a>
  <br>
  <br>
  <button @click=toggleStatus>Change status</button>
</template>