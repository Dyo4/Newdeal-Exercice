<template>
  <div>
    <button @click="getPosts">Charger requêtes</button>
    <h3 v-if="error">{{ errorMsg }}</h3>
    <div v-for="post in posts" :key="post.id">
        <h3>{{ post.id }}. {{ post.title }}</h3>
        <p>{{ post.body }}</p>
        <hr />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
  export default {
    name: 'PostList',
    data() {
        return {
            posts: [],
            errorMsg: ''
        }
    },
    methods: {
        getPosts() {
            axios
                .get('https://jsonplaceholder.typicode.com/posts')
                .then((response) => {
                    console.log(response.data)
                    this.posts = response.data
                })
                .catch((error) => {
                    console.log(error)
                    this.errorMsg= 'Erreur dans la récupération des données'
                })
        },
    },
  }
</script>

<style scoped>
</style>