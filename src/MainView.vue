
<template>
    <main>
        <h1>Hello, World!</h1>
        <div v-if="document" v-html="documentAsHtml"></div>
        <p v-else>Loading...</p>
    </main>
</template>

<script>
import axios from 'axios';
import { marked } from 'marked';

export default {

    data() {
        return {
            document: null,
        };
    },

    computed: {
        documentAsHtml() {
            return marked(this.document);
        }
    },

    methods: {

        loadDocument(url) {
            url = /\.md$/.test(url) ? url : `${url}.md`;
            console.log(`loading document: ${url}`);
            axios.get(url)
                .then(response => (this.document = response.data))
                .catch(err => console.log(`could not load url:\n${err}`));
        },

        loadCurrentDocument() {
            let doc = document.location.hash || 'index.md';
            doc = doc.replace(/\#/g, '');
            this.loadDocument(doc);
        },

    },

    created() {
        this.loadCurrentDocument();
        window.addEventListener('hashchange', (e) => {
            this.loadCurrentDocument();
        });
    }

}
</script>

