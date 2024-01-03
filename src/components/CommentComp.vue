// CommentComp.vue

<template>
  <div class="hello">
   <p>{{ value }}</p>   
   <p>Liczba polubien: {{ likes }}</p>
   <p>Czas: {{ data }}</p>
  </div>
</template>

<script>
export default {
 props: {
    value: String,
    likes: Number,
    data: Number
  }
};
</script>

<style>
  .hello{
    border: 1px solid black;
    margin: 10px 0;
    padding: 0 8px;
  }
</style>
