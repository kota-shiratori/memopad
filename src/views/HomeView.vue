<template>
  <div class="home">
    <ul v-if="hasMemos">
      <li v-for="memo in memos" :key="memo.id">
        <RouterLink :to="{ name: 'edit', params: { id: memo.id } }">
          {{ memo.title }}
        </RouterLink>
      </li>
    </ul>
    <p v-else>メモはありません</p>
  </div>
</template>

<style scoped>
ul {
  margin: 0;
  padding: 0;
}

li {
  list-style: none;
  border-bottom: solid 1px #ccc;
  padding-bottom: 10px;
  margin-bottom: 10px;
}

li a {
  color: #999;
  text-decoration: none;
  display: block;
  width: 100%;
}
</style>

<script>
export default {
  name: 'HomeView',
  computed: {
    hasMemos() {
      return this.$store.getters.getCount
    },
    memos() {
      return this.$store.getters.getAll
    }
  }
}
</script>
