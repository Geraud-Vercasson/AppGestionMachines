<template>
    <div>
        <h1>Machine {{name}}</h1>
        <h2 :class="{green: status, red: !status}">Status {{status? 'OK':'KO'}}</h2>
        <h3>Last time checked : {{checkedAt.toLocaleString()}}</h3>
    </div>
</template>

<script>
    export default {
        name: "machine",
        props: ["name", "status"],
        data: function () {
            return {
                checkedAt: new Date(),
            }
        }
    }
</script>

<style scoped>
    .red {
        color: red;
    }
    .green {
        color: green;
    }
</style>