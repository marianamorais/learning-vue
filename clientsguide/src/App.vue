<template>
  <div id="app">
    <h3 class="title navbar-brand" >Register</h3>

    <div class="inputs">
      <input type="number" placeholder="Id" class="input" v-model="clientId">
      <input type="text" placeholder="Name" class="input" v-model="clientName">
      <input type="text" placeholder="Description" class="input" v-model="clientDescription">
      <input type="text" placeholder="Email" class="input" v-model="clientEmail">
      <input type="text" placeholder="Phone" class="input" v-model="clientPhone">
      <input type="number" placeholder="Age" class="input" v-model="clientAge">
    </div>

    <p v-if="errorInput" class="errorInput">O nome é inválido, tente novamente!</p>

    <button @click="register" class="button">Register</button>

    <div v-for="(client,index) in orderClients" :key="client.id">
      <h4>{{ index + 1 }}</h4>
      <Client :client="client" @delete="deleteClient($event)"/>
    </div>

    
  </div>
</template>

<script>
import _ from 'lodash';

import Client from './components/Clients';

export default {
  name: 'App',
  data() {
    return {
      errorInput: false,
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
      if(this.clientName == "" || this.clientName.length < 3){
        
        this.errorInput = true;

        console.log("Erro de validação");
      } else {
        
        this.clients.push(
        {
          id: this.clientId,
          name: this.clientName,
          description: this.clientDescription,
          email: this.clientEmail,
          phone: this.clientPhone,
          age: this.clientAge
          
        }
      )
        this.cleanInputs()
        this.errorInput = false;
      }
    },
    cleanInputs() {
      this.clientId = ""
      this.clientName = ""
      this.clientDescription = ""
      this.clientEmail = ""
      this.clientPhone = ""
      this.clientAge = ""
    },
    deleteClient: function($event) {
      var id = $event.idClient;
      var newArray = this.clients.filter(client => client.id != id);
      this.clients = newArray;
    }
  },

  computed: {
    orderClients: function() {
      return _.orderBy(this.clients,['name'], ['asc']);
    }
  },
}

</script>

<style>
  .inputs {
    display: flex;
    flex-direction: column;
    width: 400px;
    margin-bottom: 15px;
  }

  .errorInput {
    color: red;
  }

</style>