<script setup>
import { ref, reactive, onMounted } from 'vue';

    let users = ref([]);
    let texts = ref("");
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
    function addcomment() {
      fetch('https://lab5-p379.onrender.com/api/v1/messages/', {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ text: texts._value, user: "WillTDP" })
    })
        .then(response => response.json())
        .then(title => (title.texts));
        console.log(JSON)
        users.value.push({text: texts._value, user: "WillTDP" })
    };
</script>

<template>
  <div class="thing">
    <div class="video_comments">
      <h1>Comments</h1>
    </div>
    <div class="comment_box">
      <div v-for="user in users" class="video_comments">
          <h3 >{{user.user}}</h3>
          <h2 >{{user.text}}</h2>
      </div>
    </div>
    <div class="video_comments">
      <input v-model="texts" type="text" placeholder="Enter your comment">
      <button @click="addcomment">Add Comment</button>
    </div>
  </div>
</template>

<style scoped>
.thing {
  padding:0 1rem;
}
.comment_box {
  overflow: scroll;
  overscroll-behavior-y: contain;
  scroll-snap-type: y proximity;
  max-height: 550px;
  width: 350px;
}
.video_comments h3 {
  font-size: 12px;
}
.video_comments h2 {
  font-size: 10px;
}
.video_comments h1 {
  font-size: 20px;
}
</style>
