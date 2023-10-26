<template>
    <enter-data v-model:name.checkEmpty="nameVal" v-model:age.check18="ageVal" />
</template>

<script>
import EnterData from './components/EnterData.vue'

export default {
    name: 'App',
    components: {
        EnterData,
    },

    data() {
        return {
            nameVal: null,
            ageVal: null,
        }
    },
}
</script>

<style lang="scss">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
