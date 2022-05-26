<template>
<div class="container pt-5">
    <div class="row">
            <Post v-for="(post,index) in posts" :key="index" :post="post"/>
    </div>
</div>

</template>

<script>

import Post from './Post.vue';
export default{
    name: "PostList",
    components:{
        Post,
    },
    data(){
        return{
            posts:[]
        }
    },

    methods:{
        getPosts(){
            axios.get('http://localhost:8000/api/posts')
            .then((risultato)=>{
               /*  console.log(risultato); */
                this.posts = risultato.data.data
                /* console.log(this.posts) */
            })
        }
    },
    created(){
        this.getPosts();
    }
}
</script>
