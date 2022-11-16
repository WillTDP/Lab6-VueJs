<script setup>
import { ref, onMounted } from 'vue';

    let username = ref('');
    let text = ref('');

    //onmounted
    onMounted (() => {
        const api = 'https://lab5-p379.onrender.com/api/v1/messages/';
        //const api = 'https://app.fakejson.com/q/Dt6soyE2?token=J8LA1-xpV4FBoiU5vS0n4Q';
        fetch(api)
        .then(response => response.json())
        .then (data => {
            console.log(data);
            username.value = data.videos[0].user;
            text.value = data.videos[0].text;
        })

    });
</script>

<template>
  <div class="video_comments">
    <h3>{{username}}</h3>
    <p>{{text}}</p>
  </div>
</template>

<style scoped>
.video_comments {
  padding:0 1rem;
}
</style>
