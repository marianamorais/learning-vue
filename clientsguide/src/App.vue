<template>
  <div id="app">
    <input type="number" placeholder="id" v-model="clientId">
    <input type="text" placeholder="name" v-model="clientName">
    <input type="text" placeholder="email" v-model="clientEmail">
    <input type="text" placeholder="age" v-model="clientAge">
    <button @click="save">Cadastrar</button>

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
      clientId: null,
      clientName: null,
      clientEmail: null,
      clientPhone: null,
      clientAge: null,
      client1: {
        name: "Mariana Morais",
        age: 23,
        phone: 1138232,
        email: "marianamorais.dev@gmail.com",
      },
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
    save () {
      const newClient = {
        id: this.clientId,
        name: this.clientName,
        email: this.clientEmail,
        age: this.clientAge
      }
      this.clients.push(newClient)
    }
  }
}
</script>

<style>

</style>
