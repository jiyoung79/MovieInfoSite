<template>
   <!-- html 코드 -->
   <h1>영화 정보</h1>
   <div v-for="(movie, i) in data" :key="i" class="item">
      <figure>
         <img :src="`${movie.ImgUrl}`" :alt="movie.title" />
      </figure>
      <!-- 데이터 바인딩 -->
      <!-- 속성에 값을 바인딩 할 때는 :속성명="데이터" 를 사용하면 됨(vue문법) -->
      <div class="info">
         <h3 class="title" :style="textRed">{{ movie.title }}</h3>
         <p>개봉 : {{ movie.year }}</p>
         <p>장르 : {{ movie.category }}</p>
         <button @:click="increaseLike(i)">좋아요</button>
         <span>{{ movie.like }}</span>
         <p>
            <button @:click="isModal = true">상세보기</button>
         </p>
      </div>
   </div>
   <div class="modal" v-if="isModal">
      <div class="inner">
         <h3>Detail</h3>
         <p>영화 상세 정보</p>
         <button @:click="isModal = false">닫기</button>
      </div>
   </div>
   <!-- 반복문을 사용할때는 각각의 자료를 구분하기 위한 key값이 반드시 필요 -->
   <!-- <p v-for="(item, i) in foods" :key="i">{{ item }}</p> -->
</template>

<script>
// js 코드
export default {
   name: 'App',
   data() {
      return {
         isModal: true,
         // 변수 지정
         //  foods: ['김밥', '순대', '만두']
         data: [
            {
               title: '노량',
               year: 2023,
               category: '액션, 드라마',
               textRed: 'color: red',
               like: 0,
               ImgUrl: './assets/노량.jpg',
            },
            {
               title: '아쿠아맨과 로스트 킹덤',
               year: 2023,
               category: '액션, 판타지, 어드벤처',
               like: 0,
               ImgUrl: './assets/아쿠아맨.jpg',
            },
            {
               title: '3일의 휴가',
               year: 2023,
               category: '판타지, 드라마',
               like: 0,
               ImgUrl: './assets/3일의휴가.jpg',
            },
         ],
      };
   },
   methods: {
      increaseLike(i) {
         this.data[i].like += 1;
      },
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
   padding: 20px;
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
