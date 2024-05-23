<script>
import axios from "axios"

export default {
  data() {
    return {
      personaMale: [],
      personaFemale: null,
      chat1: "",
      chat2: ""
    }
  },

  async mounted() {
    try {
      const url = "https://randomuser.me/api/?gender="

      const { data } = await axios.get(`${url}male`)
      //const {female} = await axios.get(`${url}female`)

      this.personaMale = data 
      console.log(this.personaMale);
      //this.personaFemale = female
    } catch (error) {
      console.error("Error fetching data:", error)
    }
  }
}
</script>

<template>
  <div>
    <h1>{{ personaMale?.name?.first }} {{ personaMale?.name?.last }}</h1>
  </div>
</template>

<style scoped></style>
