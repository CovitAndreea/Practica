<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/logo.svg')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h2 class="headline font-weight-bold mb-3">
          Text Input
        </h2>

        <v-row justify="center" class="ma-2">
      <v-col cols="4">
        <v-text-field 
        v-model="newmessage"
        placeholder="Write Something" 
        color="purple" 
        outlined shaped
        ></v-text-field>
        <p>Message is: {{ newmessage }}</p>
      </v-col>
        </v-row>
      
        <v-btn
        color="primary"
        elevation="2"
        >Enter</v-btn>
      </v-col>

      <v-col
        class="mb-5"
        cols="12"
      >
        
      </v-col>

      <v-col
        class="mb-5"
        cols="12"
      >
       
      </v-col>

      <v-col
        class="mb-5"
        cols="12"
      >
        
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({
      messages: [],
      newmessage: '',
    }),
    mounted() {
      if (localStorage.getItem('messages')) {
      try {
        this.messages = JSON.parse(localStorage.getItem('messages'));
      } catch(e) {
        localStorage.removeItem('messages');
      }
    }
    }, 
    methods: {
    addMessage() {
      if (!this.newmessage) {
        return;
      }

      this.messages.push(this.newmessage);
      this.newmessage = '';
      this.saveMessages();
    },
    removeMessage(x) {
      this.messages.splice(x, 1);
      this.saveMessages();
    },
    saveMessages() {
      const parsed = JSON.stringify(this.messages);
      localStorage.setItem('messages', parsed);
    }
  }
}
</script>
