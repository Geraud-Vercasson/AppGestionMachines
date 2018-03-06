<template>
  <div>
    <h2>Carte des machines</h2>
    <gmap-map
            :center="{lat:45.1815349, lng:5.7283311}"
            :zoom="2"
            style="width: 70%; height: 500px; margin: auto"
    >
      <gmap-marker v-for="machine in machines" :position="{lat:machine.latitude, lng:machine.longitude}"/>
    </gmap-map>
  </div>
</template>

<script>
    export default {
        name: "machines-map",
        props: ['machines']

    }
</script>

<style scoped>

</style>

