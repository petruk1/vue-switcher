<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.png">
        <Switcher v-bind:disabled="isDisabled"
                  @change="handleChange"
                  v-model="isActive">on/off
        </Switcher>
    </div>
</template>

<script>
    import Switcher from './components/Switcher.vue'

    export default {
        name: 'app',
        data: () => {
            return {
                isActive: false,
                isDisabled: false
            }
        },
        components: {
            Switcher
        },
        methods: {
            handleChange() {
                console.log(`isActive: ${this.isActive}`)
            }
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
