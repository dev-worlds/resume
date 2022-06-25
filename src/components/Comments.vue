<template>
  <div class="container">
    <div class="card" v-if="comments.length">
      <h2>Комментарии</h2>
      <ul class="list">
        <li class="list-item" v-for="comment in comments" :key="comment.id">
          <div>
            <p><strong>{{ comment.email }}</strong></p>
            <small>{{ comment.body }}</small>
          </div>
        </li>
      </ul>
    </div>
    <div class="loader" v-else-if="loadComments"></div>
    <p v-else>
      <button class="btn primary" @click.prevent="handleClickLoadComments">Загрузить комментарии</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "Comments",
  data() {
    return {
      comments: [],
      loadComments: false
    }
  },
  methods: {
    async handleClickLoadComments() {
      this.loadComments = true;
      const url = 'https://jsonplaceholder.typicode.com/comments?_limit=42';
      const response = await fetch(url);
      if (response.ok) {
        const json = await response.json();
        this.comments.push(...json);
      }
      this.loadComments = false;
    }
  }
}
</script>

<style scoped>

</style>