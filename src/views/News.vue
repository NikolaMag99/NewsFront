<template>
  <div class="news">
    <h1 class="mt-4">News</h1>

    <div class="row">
      <div class="col-4">
        <table class="table">
          <thead>
          <tr>
            <th scope="col">ID</th>
            <th scope="col">Title</th>
            <th scope="col">Content</th>
          </tr>
          </thead>
          <tbody>
          <tr v-for="news in newss" :key="news.id" @click="selectedNews = news">
            <th scope="row">{{ news.id }}</th>
            <td>{{ news.title | capitalize }}</td>
            <td>{{ news.content | shortText }}</td>
          </tr>
          </tbody>
        </table>
      </div>
      <div class="col-6">
        <subject v-if="selectedNews" :news="selectedNews"></subject>
      </div>
    </div>
  </div>
</template>

<script>
import News from "../components/News";

export default {
  // eslint-disable-next-line vue/no-unused-components
  components: {News},
  filters: {
    shortText(value) {
      if (value.length < 30) {
        return value;
      }
      return value.slice(0, 30) + '...'
    }
  },
  data() {
    return {
      selectedNews: null,
      newss: []
    }
  },
  mounted() {
    this.$axios.get('/api/news').then((response) => {
      this.newss = response.data;
    });
  },
}
</script>
