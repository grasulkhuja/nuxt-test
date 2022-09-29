<template>
  <div v-if="user" class="container px-5 py-5">
    <ul>
      <li v-for="[key, value] in Object.entries(user)" :key="key">
        {{ key }}: {{ value }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'UserItem',
  data() {
    return {
      user: null,
    }
  },
  created() {
    this.getUserById()
  },
  methods: {
    async getUserById() {
      const { data } = await this.$axios.get(
        'https://jsonplaceholder.typicode.com/users/' + this.$route.params.id
      )
      this.user = data
    },
  },
}
</script>
