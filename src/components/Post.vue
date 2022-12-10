<template>
    <section class="UserDate">
        <img class="user_icon" v-bind:src="post.username_source" width="25" height="25" alt="User icon">
        <p>{{post.username}}&ensp;&ensp;&ensp;</p>
        <p>{{post.date}}</p>
    </section>
    <img class="image" v-bind:src="post.img_source">
    <p>{{post.description}}</p>
    <section class="Likes">
        <button @click="AddLike()">Like</button>
        <p>{{post.likes}}</p>
    </section>
</template>

<script>
export default {
    name: "Post",
    props: {
        post: { type: Object, default: {}},
    },
    methods: {
        AddLike() {
            this.post.likes += 1;
        }
    }
}
</script>