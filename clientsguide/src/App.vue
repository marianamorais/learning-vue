<template>
  <div id="app">
    <Client :client="client1"/>
    <Client :client="client1"/>
    <Client :client="client1"/>
    <Client :client="client1"/>

    
  </div>
</template>

<script>
import Client from './components/Client';

export default {
  name: 'App',
  data() {
    return {
      clientName: "Mariana Morais",
      client1: {
        name: "Mariana Morais",
        age: 23,
        phone: 1138232
      }
    }
  },
  components: {
    Client,
  }
}
</script>

<style>

</style>
