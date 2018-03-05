<template>
    <div>
        <h2>Liste des machines</h2>
        <machine class="bordered" v-for="machine in machines" :key="machine.id" :machine="machine"/>
    </div>
</template>

<script>
    import Machine from './Machine.vue'
    export default {
        name: "machines-list",
        components: {'machine':Machine},
        data: function () {
            return {
                machines: [{
                    id: 1,
                    name: 'What else ?',
                    status: true,
                    checkedAt: new Date(),
                }, {
                    id: 2,
                    name: 'Broken',
                    status: false,
                    checkedAt: new Date(),
                }]
            }
        }
    }
</script>

<style scoped>
    .bordered {
        border: 2px solid black;
        margin: 10px;
    }
</style>