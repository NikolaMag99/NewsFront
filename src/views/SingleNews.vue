<template>
  <div>
    <subject :news="news"></subject>
  </div>
</template>

<script>
import News from "../components/News";
export default {
  name: "SingleNews",
  // eslint-disable-next-line vue/no-unused-components
  components: {News},
  data() {
    return {
      news: {},
    }
  },
  created() {
    this.$axios.get(`/api/news/${this.$route.params.id}`).then((response) => {
      this.news = response.data;
    });
  }
}
</script>

<style scoped>

</style>
