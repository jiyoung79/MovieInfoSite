<template>
   <!-- html 코드 -->
   <Navbar />
   <Event :text="text" />
   <Movies
      :data="data"
      @openModal="
         isModal = true;
         selectedMovie = $event;
      "
      @increaseLike="increaseLike($event)" />
   <Modal :data="data" :isModal="isModal" :selectedMovie="selectedMovie" @closeModal="isModal = false" />

   <!-- 반복문을 사용할때는 각각의 자료를 구분하기 위한 key값이 반드시 필요 -->
   <!-- <p v-for="(item, i) in foods" :key="i">{{ item }}</p> -->
</template>

<script>
// js 코드
import data from './assets/movies';
import Navbar from './components/Navbar.vue';
import Modal from './components/Modal.vue';
import Event from './components/Event.vue';
import Movies from './components/Movies.vue';

console.log(data);

export default {
   name: 'App',
   data() {
      return {
         isModal: false,
         // 변수 지정
         data: data,
         selectedMovie: 0,
         text: 'NETFILX 강렬한 운명의 드라마, 경성크리처',
      };
   },
   methods: {
      increaseLike(i) {
         this.data[i].like += 1;
      },
   },
   components: {
      Navbar: Navbar,
      Modal: Modal,
      Event: Event,
      Movies: Movies,
   },
};
</script>

<style>
/* css코드 */
* {
   box-sizing: border-box;
   margin: 0;
}

body {
   max-width: 768px;
   margin: 0 auto;
   /* padding: 20px; */
}

h1,
h2,
h3 {
   margin-bottom: 1rem;
}

p {
   margin-bottom: 0.5rem;
}

button {
   margin-right: 10px;
   margin-top: 1rem;
}

.item {
   width: 100%;
   border: 1px solid lightgray;
   display: flex;
   margin-bottom: 20px;
   padding: 1rem;
}

.item figure {
   width: 30%;
   margin-right: 1rem;
}

.item img {
   width: 100%;
}
.item .info {
   width: 100%;
}

.modal {
   background: rgba(0, 0, 0, 0.7);
   position: fixed;
   left: 0;
   top: 0;
   width: 100%;
   height: 100vh;
   display: flex;
   justify-content: center;
   align-items: center;
}

.modal .inner {
   background: #fff;
   width: 80%;
   padding: 20px;
   border-radius: 10px;
}
</style>
