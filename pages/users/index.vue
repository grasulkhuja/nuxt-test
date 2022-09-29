<template>
  <div class="container px-5 py-5">
    <ul v-if="users.length">
      <li v-for="user in users" :key="user.id">
        <NuxtLink :to="'users' + user.id">{{ user.name }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'UsersIndex',
  data() {
    return {
      users: [],
    }
  },
  created() {
    this.getUsers()
  },
  methods: {
    async getUsers() {
      const { data } = await this.$axios.get(
        'https://jsonplaceholder.typicode.com/users'
      )
      this.users = data
    },
  },
}
</script>
