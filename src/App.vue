
<template>
    <main-view />
</template>

<script>
import MainView from './MainView.vue';

export default {
    
    components: {
        MainView
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

        max-width: 1140px;
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

