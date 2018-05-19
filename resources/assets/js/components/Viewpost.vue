<template>
    <div>
        <h3>{{ post.title }}</h3>
        <string>Body : </string>
        <div>
            {{ post.body }}
        </div>
        <br>
        <span class="glyphicon glyphicon-arrow-left"></span>
        <router-link v-bind:to="'/'">Baack to post list</router-link>
    </div>
</template>

<script>
export default {
    data: function() {
        return {post: {title: '', body: ''}}
    },
    created: function() {
        let uri = '/posts/'+this.$route.params.id;
        Axios.get(uri,).then((response) => {
            this.post = response.data;
        })
    }
}
</script>
