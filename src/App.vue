
<template>
    <nav-bar v-if="config.navigation" :items="config.navigation" />
    <main-view />
</template>

<script>
import axios from 'axios';
import MainView from './MainView.vue';
import NavBar from './NavBar.vue';

export default {
    
    components: {
        MainView, NavBar
    },

    data() {
        return {
            config: {}
        };
    },

    created() {
        axios.get('/config.json')
            .then(response => (this.config = response.data))
            .catch(reason => console.log(`could not get site configuration\n${reason}`));
    },

}
</script>

<style>
    html { box-sizing: border-box; }
    *, *::before, *::after { box-sizing: inherit; }

    main {
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        line-height: 1.3;
        color: #111;

        max-width: 960px;
        margin: 0 auto;
    }

    a {
        --link-color: #0074D9;
        color: var(--link-color);
        text-decoration: none;
    }

    a:hover, a:focus {
        border-bottom: 1px solid var(--link-color);
    }
</style>

