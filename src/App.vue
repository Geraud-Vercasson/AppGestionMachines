<template>
  <div id="app">
    <img src="http://www.thelogofactory.com/wp-content/uploads/2015/08/coffee-services-unlimited-logo.png">
    <h1>{{ msg }}</h1>
    <h2 class="red" v-if="error != null"> une erreur est survenue : {{error}}</h2>
    <h2 v-if="loading">Chargement</h2>
    <div class="form-group">
      <label for="selectMachines">Sélectionnez les machines à afficher</label>
      <select class="form-control" id="selectMachines" v-model="shown">
        <option value="*">Toutes</option>
        <option value="OK">Actives</option>
        <option value="KO">Inactives</option>
      </select>
    </div>
    <div>
      <router-link to="/list" class="btn btn-primary">Accéder à la liste des machines</router-link>
      <router-link to="/map" class="btn btn-primary">Accéder à la carte des machines</router-link>
    </div>
    <br>
    <div>
      <ajout-machine v-on:success="getMachineList"/>
    </div>
    <router-view :machines="machinesFilter(shown)" :position="myPosition"/>

  </div>
</template>

<script>
  import axios from 'axios'

  export default {

    name: 'app',
    data: function () {
      return {
        msg: 'Bienvenue dans la gestion du parc de machines!',
        listeMachines: [], // au début la liste des machines est vide
        loading: false,
        error: null,
        myPosition: {lat: 0, lng: 0},
        shown: '*'
      }
    },
    created() {
      this.getMachineList()
    },
    methods: {
      machinesFilter(toShow) {
        if (toShow === "OK") {
          return this.listeMachines.filter(function (machine) {
            return machine.status === "true"
          })
        }
        else if (toShow === "KO") {
          return this.listeMachines.filter(function (machine) {
            return machine.status === "false"
          })
        }
        else if (toShow === "*") {
          return this.listeMachines
        }
        else {
          return [];
        }
      },
      getMachineList(){
        this.loading = true
        axios.get('https://machine-api-campus.herokuapp.com/api/machines').then(response => {
          this.loading = false
          this.listeMachines = response.data
        }).catch(error => {
          this.error = error;
        });
        window.navigator.geolocation.getCurrentPosition(pos => {
          this.myPosition = {
            lat: pos.coords.latitude,
            lng: pos.coords.longitude
          }
        })
      }
    }
  }
</script>

<style scoped>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin: auto;
    margin-top: 60px;
    width: 80%;
  }

  img {
    width: 200px;
    height: 200px;
  }

  h1, h2 {
    font-weight: normal;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }
  .red{
    color: red;
    font-weight: bold;
    text-transform: uppercase;
  }
</style>
