
<template>
    <nav class="navbar">
        <ul>
            <li v-for="item in items"
                :key="item.title"
            >
                <a :href="url(item.url)">
                    {{ item.title }}
                </a>
            </li>
        </ul>
    </nav>
</template>

<script>
export default {
    
    props: ['items'],

    methods: {

        url(document) {
            return `#${document}`;
        },

    },

}
</script>

<style>
    .navbar ul {
        list-style: none;
        display: flex;
    }

    .navbar a {
        display: block;
        padding: 1rem 2rem;
        color: #111;
        font-weight: 550;
        background-color: #FCA17D;
    }

    .navbar a:hover, .navbar a:focus {
        border-bottom: none;
        background-color: #FDC5AF;
    }
</style>

