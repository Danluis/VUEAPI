<template>
    <h1>Listado Posts</h1>
    <ul class="postsList">
        <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
        </ul>
</template>

<script>
import {defineComponent, onMounted} from 'vue'
import PostService from '@/services/PostService'

export default defineComponent({
    name:'PostList',

    setup() {
        const service = new PostService();
        const posts = service.getPosts();

        onMounted(async () => {
            await service.fetchAll()
        })
        return {posts}
    }
    
})

</script>

<style scoped lang="scss">
.postsList {
    width: 95vw;
    height: 75px;
    padding: 20px;
    list-style-type: none;

    li{
    padding: 10px;
    width: 100%;
    border: 1px solid #ccc;
    color: $green;
}
    li:hover {
        background-color: darken(#000000, 10%);
    }
}

</style>