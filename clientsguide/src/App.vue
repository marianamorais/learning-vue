<template>
  <div id="app">
    <h3>Register</h3>

    <div class="inputs">
      <input type="number" placeholder="Id" v-model="clientId">
      <input type="text" placeholder="Name" v-model="clientName">
      <input type="text" placeholder="Description" v-model="clientDescription">
      <input type="text" placeholder="Email" v-model="clientEmail">
      <input type="text" placeholder="Phone" v-model="clientPhone">
      <input type="number" placeholder="Age" v-model="clientAge">
    </div>
    <button @click="register">Register</button>

    <div v-for="client in clients" :key="client.id">
      <Client :client="client" />
    </div>

    
  </div>
</template>

<script>
import Client from './components/Clients';

export default {
  name: 'App',
  data() {
    return {
      clientId: Date.now(),
      clientName: null,
      clientDescription: null,
      clientEmail: null,
      clientPhone: null,
      clientAge: null,
     
      clients: [
        { 
          id: 0,
          name: "Mariana Morais",
          email: "marianamorais.dev@gmail.com",
          age: 23
        },
        { 
          id: 1,
          name: "João Victor",
          email: "joaovictor.dev@gmail.com",
          age: 23
        },
        { 
          id: 2,
          name: "Lila",
          email: "lila.dev@gmail.com",
          age: 23
        },
        { 
          id: 3,
          name: "234234",
          email: "234234.dev@gmail.com",
          age: 234
        }
      ]
    }
  },
  components: {
    Client, 
  },
  methods: {
    register() {
      const newClient = {
        id: this.clientId = "",
        name: this.clientName = "",
        description: this.clientDescription = "",
        email: this.clientEmail = "",
        phone: this.clientPhone = "",
        age: this.clientAge = ""
      }
      this.clients.push(newClient)
    }
  }
}
</script>

<style>
  .inputs {
    display: flex;
    flex-direction: column;
    width: 400px;
    margin-bottom: 15px;
  }
</style>
