<script setup>
//let src = 'https://www.youtube.com/embed/fjDbzlTcsBg'
//let src = 'https://vue-3-tiktok.vercel.app/video1.mp4';

import {ref, reactive, onMounted } from 'vue';
import 'animate.css';

let src = ref('');

let videos = reactive({videos:[]});

let animation = ref('');

//onmounted
onMounted (() => {
  console.log('mounted');
  //console.log(src);
  //fetch from api
     let api_url = 'http://127.0.0.1:5173/toktik.json';
   //let api_url = 'https://app.fakejson.com/q/Dt6soyE2?token=J8LA1-xpV4FBoiU5vS0n4Q';
    fetch(api_url)
    .then(response => response.json())
    .then (data => {
      console.log(data);
      src.value = data.videos[0].video;
      videos.videos = data.videos;
    })
});

const nextVideo = () => {
  console.log('next video');
  animation.value = 'animate__animated   animate__bounceInDown ';
  src.value = videos.videos[1].video;
  animation.value = 'animate__animated   animate__bounceInUp ';

}
 </script>

<template>
  <div class="video">
    <div class="controls">
        <a @click.prevent="nextVideo" href="#" class="controls_next">⬇️</a>
    </div>
    <video :class="animation"  :src="src" controls autoplay>
    </video>
  </div>
</template>

<style scoped>
.video {
  position: relative;
  right: 2em;
  top: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.controls {
  position: absolute;
  top: 0;
  right: 0;
}
</style>
