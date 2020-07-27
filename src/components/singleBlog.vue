<template>
    <div id="single-blog">
        <h1>{{blog.title}}</h1>
        <article>{{blog.body}}</article>
    </div>
</template>

<script>
const axios = require('axios');
    export default {
        data() {
            return {
                id: this.$route.params.id,
                blog: {},
            }
        },
        created() {
            axios.get('https://jsonplaceholder.typicode.com/posts/'+this.id).then((result) => {
                console.log(result)
                this.blog = result.data
            }).catch((err) => {
                console.log(err)
            });
        },
    }
</script>

<style scoped>

</style>