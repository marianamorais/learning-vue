<template>
  <div :class="{'client': !isPremium, 'client-premium': isPremium}" class="card"> 
    <h2 class="card-header-title">Client info</h2>
    <div class="content">
      <p>Description: {{ client.description }}</p>
      <p>Name: {{ client.name }}</p>
      <p v-if="showAge === true">Age: {{ client.age }}</p>
      <p>Email: {{ client.email.toUpperCase() }}</p>
      <p>Phone: {{ client.phone }}</p>
      <p>Especial Id: {{ EspeialId }}</p>
      <button @click="changeColor" class="button is-light">Change color</button>
      <button @click="deleteCard" class="button is-light">Delete</button>
    </div>
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
    },
    deleteCard: function() {
      console.log("Emitindo do filho!")
      this.$emit("delete", {idClient: this.client.id, component: this});
    },
  },

  computed: {
    EspecialId: function() {
      return (this.client.email + this.client.name + this.client.id).toUpperCase();
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