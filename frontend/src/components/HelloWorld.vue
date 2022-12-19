<script setup>

defineProps({
    msg: String,
    test: String,
})
</script>

<template>
    <h1>{{ msg }}</h1>
    <h2>{{ test }}</h2>
</template>

<style scoped>
h2{
    color:red;
}
</style>
