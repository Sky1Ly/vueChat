<script>
import axios from "axios"
import ChatComp from "./components/ChatComp.vue";

export default {
  data() {
    return {
      users: [],
      chat1: "",
      chat2: "",
      colorChat1: "#CCCCCC",
      colorChat2: "#78db76",
      chatTemporal1: "",
      chatTemporal2: ""
    }
  },

  components: {
    ChatComp
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
    },

    updateChat(chat){
      if (chat === 1) {
        this.chatTemporal1 = this.chat1
      } else {
        this.chatTemporal2 = this.chat2
      }
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
      
      <div class="col-sm-3 d-flex justify-content-center align-items-center">
        <div v-for="(user, i) in users" :key="i">
          <div v-if="i == 0" class="content-center">
            <img :src="user.picture?.large" alt="" srcset="">
            <h1 class="tex-center">{{ user.name?.first }}</h1>
            <label for="myColor" class="form-label">Seleccine color</label>
            <input type="color" class="form-control form-control-color" id="myColor" v-model="colorChat1">
            <textarea class="mt-3" name="Chat" v-model="chat1" rows="3"></textarea>
            <button type="button" class="btn btn-success mt-3" @click="updateChat(1)">Enviar</button>
          </div>
        </div>
      </div>

      <ChatComp :chatPrincipal="chatTemporal1" :chatSecundario="chatTemporal2" :colorChatPrincipal="colorChat1" :colorChatSecundario="colorChat2"/>

      <div class="col-sm-3 d-flex justify-content-center align-items-center">
        <div v-for="(user, i) in users" :key="i">
          <div v-if="i == 1" class="content-center">
            <img :src="user.picture?.large" alt="" srcset="">
            <h1 class="tex-center">{{ user.name?.first }}</h1>
            <label for="myColor" class="form-label">Seleccine color</label>
            <input type="color" class="form-control form-control-color" id="myColor" v-model="colorChat2">
            <textarea class="mt-3" name="Chat" v-model="chat2" rows="3"></textarea>
            <button type="button" class="btn btn-primary mt-3" @click="updateChat(2)">Enviar</button>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<style>
.content-center {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.tex-center {
  text-align: center;
}
</style>
