<template>
  <div :class="{'client': !isPremium, 'client-premium': isPremium}"> 
    <h2>Client info</h2>
    <p>Description: {{ client.description }}</p>
    <p>Name: {{ client.name }}</p>
    <p v-if="showAge === true">Age: {{ client.age }}</p>
    <p>Email: {{ client.email }}</p>
    <p>Phone: {{ client.phone }}</p>
    <button @click="changeColor">Change color</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isPremium: false,
    }
  },

  methods: {
    changeColor: function() {
      this.isPremium = !this.isPremium;
    }
  },

  props: {
    client: Object,
    showAge: Boolean
  }
}
</script>
  
<style scoped>
  .client {
    max-width: 1000px;
    padding: 30px;
    background: #F6907A;
    border: 1px solid #F6907A;
    border-radius: 8px;
    margin: 20px;
  }

  .client-premium {
    max-width: 1000px;
    padding: 30px;
    background: #363232;
    border: 1px solid #363232;
    border-radius: 8px;
    color: #F6907A;
    margin: 20px;
  }
</style>