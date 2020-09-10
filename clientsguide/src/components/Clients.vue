<template>
  <div id="client"> 
    <h2>Client info</h2>
    <hr>
    <p>Description: {{ client.description }}</p>
    <p>Name: {{ client.name }}</p>
    <p>Age: {{ client.age }}</p>
    <p>Email: {{ client.email }}</p>
    <p>Phone: {{ client.phone }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      
    }
  },

  props: {
    id: Number,
    name: String,
    email: String,
    phone: Number,
    age: Number,
    description: String,
    client: Object
  }
}
</script>
  
<style scoped>
  #client {
    max-width: 1000px;
    padding: 30px;
    background: #F6907A;
    border: 1px solid #F6907A;
    border-radius: 8px;
    margin: 20px;
  }
</style>