<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <button @click="sendMessage('Hi, there')">Connect Socket</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      connection: null,
    }
  },
  methods: {
    sendMessage (message) {
      console.log(this.connection);
      this.connection.send(message);
    }
  },
  created () {
    console.log("Strating Connection to WebSocket Server");
    this.connection = new WebSocket("wss://echo.websocket.org");

    this.connection.onopen = function(event) {
      console.log(event);
      console.log("Successfully Connected to the Echo WebSocket Server");
    }

    this.connection.onmessage = function(event) {
      console.log(event);
    }
  }
}
</script>
