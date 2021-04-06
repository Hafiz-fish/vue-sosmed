<template>
    <div class="user-profile">
        <div class="user-profile__user-panel">
            <h1 class="user-profile__username">@{{ user.username }}</h1>
            <div class="user-profile__admin-badge" v-if="user.isAdmin">
                Admin
            </div>
            <div class="user-profile__follower-count">
                <strong>Followers: </strong> {{ followers }}
            </div>
            <form action="" class="user-profile__create-post">
                <label for="newPost">
                    <strong>New Post</strong>
                </label>
                <textarea name="" id="newPost" rows="4"></textarea>
                <div class="user-profile__create-post-type">
                    <label for="newPostType">
                        <strong>Type:</strong>
                    </label>
                    <select name="" id="newPostType">
                        <option :value="option.value" v-for="(option, index) in postTypes" :key="index">
                            {{ option.name }}
                        </option>
                    </select>
                </div>
            </form>
        </div>
        <div class="user-profile__posts-wrapper">
           <PostItem v-for="post in user.posts" :key="post.id" :username="user.username" :post="post" @favourite="toggleFavourite"/>
        </div>
    </div>
</template>

<script>
import PostItem from './PostItem.vue'

export default {
    name: 'UserProfile',
    components: {
        PostItem
    },
    data() {
        return {
            postTypes: [
                { value: 'draft', name: 'Draft'},
                { value: 'instant', name: "Instant Post"}
            ],
            followers: 0,
            user: {
                id: 1,
                username: 'Jakos_me',
                firstName: 'Jake',
                lastName: 'Kosasi',
                email: 'Jakekos@email.com',
                isAdmin: true,
                posts: [
                    {
                        id: 1,
                        content: 'My first post in here'
                    },
                    {
                        id: 2,
                        content: 'Morning ma world!'
                    }
                ]
            }
        }
    },
    watch: {
        followers(newFollowerCount, oldFollowerCount) {
            if (oldFollowerCount < newFollowerCount) {
                console.log(`${this.user.username} has gained follower!`);
            }
        }
    },
    computed: {
        fullName() {
            return `${this.user.firstName} ${this.user.lastName}`;
        }
    },
    methods: {
        followUser() {
            this.followers++;
        },
        toggleFavourite(id) {
            console.log(`Fav ${id}`)
        }
    },
    mounted() {
        this.followUser();
    }
}
</script>

<style>
.user-profile {
    display: grid;
    grid-template-columns: 1fr 3fr;
    width: 100%;
    padding: 50px 5%;
}

.user-profile__user-panel {
    display: flex;
    flex-direction: column;
    margin-right: 50px;
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 1px solid rgb(236, 236, 236);
}

h1 {
    margin: 0;
}

.user-profile__admin-badge {
    background-color: rgb(17, 66, 139);
    color: white;
    margin-right: auto;
    padding: 0 10px;
    border-radius: 5px;
    font-weight: bold;
    font-size: 15px;
    margin-top: 5px;
    margin-bottom: 10px;
}

.user-profile__create-post {
    display: flex;
    padding-top: 10px;
    border-top: 1px solid #ddd;
    flex-direction: column;
    margin-top: 10px;
}
</style>