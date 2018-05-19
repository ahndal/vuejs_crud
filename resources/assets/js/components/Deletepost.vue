<template id="post-delete">
    <div>
        <h3>Delete Post {{ post.title }}</h3>

        <form v-on:submit.prevent="deletePost">
            <p>The action cannot be undone</p>

            <button type="submit" class="btn btn-xs btn-danger">Delete Post</button>
            <router-link class="btn btn-xs btn-primary" v-bind:to="'/'">Back</router-link>
        </form>
    </div>
</template>


<script>
export default {
    data: function() {
        return {post: {title: '', body: ''}}
    },
    created: function() {
        let uri = '/posts/'+this.$route.params.id+'/edit';
        Axios.get(uri,).then((response) => {
            this.post = response.data;
        })
    },
    methods: {
        deletePost: function() {
            let uri = '/posts/'+this.$route.params.id;
            Axios.delete(uri, this.post).then((response) => {
                this.$router.push({name: 'Listposts'})
            })
        }
    }
}
</script>
