<script setup>
import { ref, onMounted } from 'vue';

    let username = ref('');
    let description = ref('');

    //onmounted
    onMounted (() => {
        //const api = 'http://127.0.0.1:5173/toktik.json';
        const api = 'https://app.fakejson.com/q/Dt6soyE2?token=J8LA1-xpV4FBoiU5vS0n4Q';
        fetch(api)
        .then(response => response.json())
        .then (data => {
            console.log(data);
            username.value = data.videos[0].username;
            description.value = data.videos[0].description;
        })

    });
</script>

<template>
  <div class="video_details">
    <h3>{{username}}</h3>
    <p>{{description}}</p>
  </div>
</template>

<style scoped>
.video_details {
  padding:0 1rem;
}
</style>
