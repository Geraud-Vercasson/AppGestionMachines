<template>
    <div>
        <h2>Liste des machines</h2>
        <machine name="What Else?" :status="false"/>
    </div>
</template>

<script>
    import Machine from './Machine.vue'
    export default {
        name: "machines-list",
        components: {'machine':Machine}
    }
</script>

<style scoped>

</style>