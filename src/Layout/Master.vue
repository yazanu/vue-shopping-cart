<template>
    <div>
        <Nav/>
        <slot></slot>
    </div>
</template>

<script>
import Nav from '../Layout/Nav.vue'
    export default {
        name: "Master",
        components: {Nav}
    }
</script>

<style lang="scss" scoped>

</style>