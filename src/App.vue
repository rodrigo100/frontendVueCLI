<template>
  <div id="app">
   <button @click="fetchUsers">Show</button>
  <ul v-for="user in users" :key="user.id">
    <li>{{user.nombre}}</li>
  </ul>
  <!-- <hello-world/> -->
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app",
  components: {
    HelloWorld
  },
    data () {
    return {
      users: [],
     
    }
  },
  ready: function() {
        console.log('test');
    },
  methods: {
    fetchUsers: function () {
      const baseURI = 'http://localhost:8080/api/v1/usuarios'
      // const baseURI = 'http://apilaravel.test/api/v1/sellers/'
      this.$http.get(baseURI)
      .then((result) => {
         this.users = result.data
        // console.log(result);
      })
    },
    mounted () {
      this.fetchUsers();
  },
  created ()
  {
    alert("hola");
  }
  
  }



};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
