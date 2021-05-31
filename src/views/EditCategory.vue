<template>
  <div class="pt-5">
    <h1 class="mt-4">Edit Category</h1>

    <table class=" table text-center" style="width: 650px;margin-left: -150px;">

      <thead>
      <tr>
        <th scope="col">Name</th>
        <th scope="col">Desc</th>
      </tr>
      </thead>

      <tbody >

      <tr v-for="category in kategorija" :key="category.name" >

        <b-card style="margin-top: 10px">
          <td scope="row"> {{ category.name }}</td>
        </b-card>
        <td scope="row"> {{ category.description }}</td>

      </tr>

      </tbody>

    </table>

        <form method="post" v-on:submit.prevent = "editCategory()" >
          <div class="form-group">
            <label for="ime">Ime</label>
            <input style="margin-top: 10px;" required  v-model="name" type="text" class="form-control" id="ime" placeholder="Enter name">
          </div>
          <div class="form-group">
            <label for="opis" style="margin-top: 10px;">Opis</label>
            <input style="margin-top: 10px;" required  v-model="description" type="text" class="form-control" id="opis" placeholder="Enter desc">

          </div>
          <br>

          <button type="submit" class="btn btn-primary mt-2">Izmeni</button>
        </form>
      </div>
</template>
<script>

export default {
  name: "EditCategory",
  data() {
    return {
      kategorija: [],
      name: null,
      description: null,
    }
  },
  mounted() {
    this.$axios.get(`/api/category/${this.$route.params.name}`).then((response) => {
      console.log("CAOOO")
      this.kategorija = response.data;
    });
  },
  methods: {
    editCategory() {
      this.$axios.post(`/api/category/${this.$route.params.name}`, {
        "name": this.name,
        "description": this.description
      }).then((response) => {
        this.kategorija = response.data;
      });
    },
  }
}
</script>

<style scoped>

</style>
