<template>
    <div id="btn">
        <button @click="getPosts">Caricamento Post...</button>
        <h3 v-if="errorMsg">{{ errorMsg }}</h3>
        <div v-for="post in posts" :key="post.id">
            <h3>{{ post.id }}, {{ post.title }}</h3>
            <p>{{ post.body }}</p>
            <hr>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
export default{
    name:'PostList',
    data(){
        return{
            posts:[],
            errorMsg:'',
        }
    },
    methods:{
        getPosts(){
            axios.get('https://jsonplaceholder.typicode.com/posts')
            .then((response) =>{
                console.log(response.data);
                this.posts=response.data
            })
            .catch((error)=>{
                console.log(error);
                this.errorMsg='Non è stato possibile caricare nessun Post'
            })
        }
    }
}
</script>

<style scoped>

</style>