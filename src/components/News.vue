<template>
  <div>
    <h2>
      Predmet: {{ news.title }}
    </h2>

    <h5>Opis:</h5>
    <p>
      {{ news.content }} <br><br>
    </p>
  </div>
</template>

<script>

export default {
  name: "News",
  props: {
    news: {
      type: Object,
      required: true,
    }
  },
}
</script>

<style scoped>

</style>
