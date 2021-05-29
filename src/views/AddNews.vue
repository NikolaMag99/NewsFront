<template>
  <div class="pt-5">
    <form @submit.prevent="login" >
      <div class="form-group">
        <label for="title">Naslov</label>
        <input style="margin-top: 10px;" v-model="title" type="text" class="form-control" id="title" placeholder="Enter title">
      </div>
      <div class="form-group">
        <label for="content" style="margin-top: 10px;">Content</label>
        <textarea style="margin-top: 10px;" cols="40" rows="5" v-model="content" type="text" class="form-control" id="content" placeholder="Enter content">
     </textarea>
      </div>
<br>
      <div >
        <date-picker v-model = "date" lang = "en" type="date" format = "dd-MM-YYYY"></date-picker>
      </div>
      <br>

<!--      <div class="form-group">-->
<!--        <label for="author">Author</label>-->
<!--        <input v-model="name" type="text" class="form-control" id="author" placeholder="Enter author">-->
<!--      </div>-->
<!--      <div class="form-group">-->
<!--        <label for="author">Category</label>-->
<!--        <input v-model="name" type="text" class="form-control" id="kategorija" placeholder="Enter author">-->
<!--      </div>-->
      <button type="submit" class="btn btn-primary mt-2">Add News</button>
    </form>

  </div>
</template>

<script>
import DatePicker from 'vue2-datepicker';

export default {
  name: "AddNews",
  components: {
    DatePicker
  },
  data() {
    return {
      date: ''
      // email: '',
      // password: '',
    }
  },
  methods: {
    // login() {
    //   this.$axios.post('/api/users/login', {
    //     email: this.email,
    //     password: this.password,
    //   }).then(response => {
    //     localStorage.setItem('jwt', response.data.jwt)
    //     this.$router.push({name: 'News'});
    //   })
    // }
  }
}
</script>

<style scoped>

</style>
