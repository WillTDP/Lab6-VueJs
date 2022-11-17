<script setup>
import { ref, onMounted } from 'vue';

    let users = ref([]);

    //onmounted
    onMounted (() => {
        const api = 'https://lab5-p379.onrender.com/api/v1/messages/';
        //const api = 'https://app.fakejson.com/q/Dt6soyE2?token=J8LA1-xpV4FBoiU5vS0n4Q';
        fetch(api)
        .then(response => response.json())
        .then (data => {
            console.log(data);
            users.value = data;

        })

    });
</script>

<template>
  <div v-for="user in users" class="video_comments">
    <h3 >{{user.user}}</h3>
    <h2 >{{user.text}}</h2>
  </div>
</template>

<style scoped>
.video_comments {
  padding:0 1rem;
}
</style>
