<template>
  <div>
    <h2>Carte des machines</h2>
    <gmap-map
            :center="{lat:10, lng:10}"
            :zoom="7"
            style="width: 100%; height: 800px"
    >
    </gmap-map>
  </div>
</template>

<script>
    export default {
        name: "machines-map",
        data: function () {
            return{
                data: require("../config.json").myAPIkey
            }
        }
    }
</script>

<style scoped>

</style>
