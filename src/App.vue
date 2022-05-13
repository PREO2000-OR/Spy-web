<template>
  <v-app>

    <v-main>
      <v-container class="">
          <v-row>
            <v-col cols="10" sm="10">
              <router-view v-bind:msgs="msgs" />
            </v-col>
          </v-row>
        </v-container>
      <v-form style="height: 95%;">
        <v-container class="textContainer">
          <v-row style="position : fixed;">
            <v-col cols="10" sm="10">
              <v-text-field v-model="message" label="Outlined" outlined clearable></v-text-field>
            </v-col>
            <v-col cols="2" sm="2">
              <v-btn @click="sendMessage" class="sendButton">Send</v-btn>
            </v-col>
          </v-row>
        </v-container>
      </v-form>
    </v-main>
  </v-app>
</template>

<script src="/socket.io/socket.io.js"></script>
<script>
const { io } = require("socket.io-client");
const socket = io("http://192.168.1.74:3000", {
  extraHeaders: {
    "my-custom-header": "abcd"
  }
});

export default {
  name: "App",
  mounted() {
    console.log(this.$store.state);
    this.run();
  },

  data: () => ({
    msgs: [],
    message: ""
  }),
  methods: {
    run() {
      socket.on("connect", () => {
        console.log(socket.id); // x8WIv7-mJelg7on_ALbx
      });
    },
    sendMessage(){
      console.log(this.message);
      socket.emit("chat message", this.message);
      socket.on("messages", data => {
        this.msgs = data.messages
      });
    },
  }
};
</script>
<style lang="css">
  .textContainer{
    display: flex;
    width: 100%;
    height: 100%;
    z-index: 1;
    flex-direction: row;
    position: fixed;
  }
  .sendButton{
    width: 100%;
    height: 100%
  }
</style>