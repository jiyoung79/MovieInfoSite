<template>
   <div class="container">
      <h1>영화 정보</h1>
      <div v-for="movie in data" :key="movie.id" class="item">
         <figure>
            <img :src="`${movie.ImgUrl}`" :alt="movie.title" />
         </figure>
         <!-- 데이터 바인딩 -->
         <!-- 속성에 값을 바인딩 할 때는 :속성명="데이터" 를 사용하면 됨(vue문법) -->
         <div class="info">
            <h3 class="title" :style="textRed">{{ movie.title }}</h3>
            <p>개봉 : {{ movie.year }}</p>
            <p>장르 : {{ movie.category }}</p>
            <button @click="$emit('increaseLike', movie.id)">좋아요</button>
            <span>{{ movie.like }}</span>
            <p>
               <button @click="$emit('openModal', movie.id)">상세보기</button>
            </p>
         </div>
      </div>
   </div>
</template>
<script>
export default {
   name: 'MoviesComponents',
   props: {
      data: Array,
   },
};
</script>
<style>
.container {
   padding: 20px;
}
</style>
