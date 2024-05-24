<script>
import axios from "axios"

export default {
  data() {
    return {
      users: [],
      chat1: "",
      chat2: ""
    }
  },

  methods: {
    async usersDataAPI(user) {
      try {
        const url = "https://randomuser.me/api/?gender="

        const { data } = await axios.get(`${url}${user}`)
        return data.results

      } catch (error) {
        console.error("Error fetching data:", error)
      }

      console.log(this.users);
    }
  },

  async mounted() {
    const maleUser = await this.usersDataAPI("male")
    const femaleUser = await this.usersDataAPI("female")

    this.users = [...maleUser, ...femaleUser]
  }
}
</script>

<template>
  <div class="container">

    <div class="row mt-5">
      
      <div class="col-sm-3">
        <div v-for="(user, i) in users" :key="i">
          <div v-if="i == 0">
            <h1>{{ user.name?.first }}</h1>
            <img :src="user.picture?.large" alt="" srcset="">
          </div>
        </div>
      </div>

      <div class="col-sm-6">
        <h1>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto quos similique magnam enim amet ratione,
          earum a veritatis voluptatum facere error illum ex vitae sequi totam deserunt eligendi et maiores?</h1>
      </div>

      <div class="col-sm-3">
        <div v-for="(user, i) in users" :key="i">
          <div v-if="i == 1">
            <h1>{{ user.name?.first }}</h1>
            <img :src="user.picture?.large" alt="" srcset="">
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<style scoped></style>
