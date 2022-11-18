<template>
    <div>
        Dasboard
    </div>
    <div>
        <span>User data length : {{user?.data?.length}}</span>
        <br />
        <span>User Data Pending : {{user?.pending}} </span> 
        <br />
        <span>User Data Error : {{user?.error?.toString()}} </span> 

    
    </div>
    <br />
    <div>
        <span>Post data length : {{post?.data?.length || 0}}</span>
        <br />
        <span>Post Data Pending : {{post?.pending}} </span> 
        <br />
        <span>Post Data Error : {{post?.error}} </span> 

        </div>

        <NuxtLink to="/" class="">back </NuxtLink>

</template>

<script setup>
const post = ref();
const user = ref();

const fetchPost = async () => {
    post.value = await useFetch('https://jsonplaceholder.typicode.com/posts');
};

const fetchUser = async () => {
    user.value = await useFetch('https://jsonplaceholder.typicode.com/users');
};
await fetchUser();

onMounted(async () => {
await fetchPost();

});
</script>

<style scoped>

</style>