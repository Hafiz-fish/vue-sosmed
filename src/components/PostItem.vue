<template>
    <div class="post-item" @click="favouritePost(post.id)">
        <div class="user-profile__post">
            <div class="post-item__user">
                @{{ username }}
            </div>
            <div class="post-item__content">
                {{ post.content }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'PostItem',
    props: {
        username: {
            type: String,
            required: true
        },
        post: {
            type: String,
            required: true
        }
    },
    methods: {
        favouritePost(id) {
            this.$emit('favourite', id);
        }
    }
}
</script>

<style>
.post-item {
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 1px solid #dfe3e8;
    box-sizing: border-box;
    cursor: pointer;
    transition: all 0.25s ease;
}

.post-item:hover {
    transform: scale(1.1, 1.1);
}

.post-item__user {
    font-weight: bold;
}
</style>