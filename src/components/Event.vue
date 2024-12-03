<template>
   <div class="event" :class="{ show: isOpen }">
      <p>{{ text }}</p>
      <button @click="isOpen = false">X</button>
   </div>
</template>
<script>
export default {
   name: 'EventComponent',
   props: {
      text: String, // 자료형 명시
      isEventOpen: Boolean,
   },
   data() {
      return {
         isOpen: true,
      };
   },
};
</script>
<style>
.event {
   background: rgb(80, 79, 79);
   color: white;
   padding: 10px 20px;
   text-align: center;
   font-size: small;
   display: flex;
   justify-content: space-between;
   align-items: center;
   display: none;
}
.show {
   display: flex;
}
.event p {
   margin: 0;
   font-size: 0.9rem;
}
.event button {
   margin: 0;
}
</style>
