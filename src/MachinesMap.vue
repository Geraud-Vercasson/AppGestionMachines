<template>
  <div>
    <h2>Carte des machines</h2>
    <gmap-map
            :center="position"
            :zoom="8"
            style="width: 70%; height: 500px; margin: auto"
    >
      <gmap-marker v-for="machine in machines" :key="machine.id" :position="{lat:parseFloat(machine.latitude), lng:parseFloat(machine.longitude)}" :clickable="true"/>
    </gmap-map>
  </div>
</template>

<script>
    export default {
        name: "machines-map",
        props: ['machines', 'position']

    }
</script>

<style scoped>

</style>

