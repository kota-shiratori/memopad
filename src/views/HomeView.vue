<template>
  <div class="home">
    <ul v-if="hasMemos">
      <li v-for="memo in memos" :key="memo.id">
        <RouterLink :to="{ name: 'edit', params: { id: memo.id } }">
          {{ memo.title }}
        </RouterLink>
      </li>
    </ul>
    <p class="no-memo" v-else>メモはありません。<router-link to="/new">メモを追加</router-link></p>
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

li a:hover {
  color: #42b983;
}

.no-memo a {
  background-color: #42b983;
  border-radius: 10px;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  padding: .5em 1em;
  color: #fff;
  border: none;
  cursor: pointer;
  font-weight: bold;
  width: fit-content;
  text-decoration: none;
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
