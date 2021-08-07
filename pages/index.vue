<template>
  <section class="contianer">
    <div>
      <input v-model.trim="todo" @keyup.enter="addTodo()" type="text" />
      <button @click="addTodo()">+ add</button>
    </div>
    <div>
      <h3>Todos</h3>
      <ul>
        <template v-for="(item, index) in todos">
          <li :key="index">
            <input type="checkbox" v-model="item.complete" />
            {{ item.title }}
          </li>
        </template>
      </ul>
    </div>

    <hr />
    <h2>Users</h2>
    <hr />
    <ul>
      <template v-for="(item, index) in users">
        <li :key="index">
          {{ item.name }}
          <p>
            {{ item.email }}
          </p>
        </li>
      </template>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      users: [],
      todos: [],
      todo: '',
    }
  },
  mounted() {
    this.todo = 'test'
    this.addTodo()
    this.getUsers()
  },
  methods: {
    addTodo() {
      if (!this.todo) {
        return
      }
      this.todos = [
        ...this.todos,
        {
          id: this.todos.length + 1,
          title: this.todo,
          complete: false,
        },
      ]
      this.todo = ''
    },
    async getUsers() {
      try {
        const req = await this.$axios.get(
          'https://jsonplaceholder.typicode.com/users'
        )
        this.users = req.data
      } catch (error) {}
    },
  },
}
</script>
<style scoped>
.contianer {
  max-width: 400px;
  margin: 0 auto;
}
</style>
