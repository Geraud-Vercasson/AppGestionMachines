<template>
    <div>
        <h1>Machine {{machine.name}}</h1>
        <h2 :class="{green: machine.status, red: !machine.status}">Status {{machine.status? 'OK':'KO'}}</h2>
        <h3>Last time checked : {{machine.checkedAt.toLocaleString()}}</h3>
    </div>
</template>

<script>
    export default {
        name: "machine",
        props: ["machine"]
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