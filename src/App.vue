<template>
    <div id="app">
        <img src="http://www.thelogofactory.com/wp-content/uploads/2015/08/coffee-services-unlimited-logo.png">
        <h1>{{ msg }}</h1>
        <button class="btn btn-primary" @click="onMachinesListClick">Accéder à la liste des machines</button>
        <button class="btn btn-primary" @click="onMapClick">Accéder à la carte des machines</button>

    </div>
</template>

<script>
    export default {
        name: 'app',
        data() {
            return {
                msg: 'Bienvenue dans la gestion du parc de machines!'
            }
        },
        methods: {
            onMachinesListClick: function () {
                alert("Tu veux la liste? Filou")
            }
            ,
            onMapClick: function () {
                alert("Tu veux la carte? Gredin")
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
        margin-top: 60px;
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
</style>
