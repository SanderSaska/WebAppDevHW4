<template>
    <section class="UserDate">
        <img class="user_icon" v-bind:src="post.username_source" width="25" height="25" alt="User icon">
        <p>{{post.username}}&ensp;&ensp;&ensp;</p>
        <p>{{post.date}}</p>
    </section>
    <p>{{post.description}}</p>
</template>

<script>
export default {
    name: "Post",
    props: {
        post: { type: Object, default: {}},
    },
}
</script>