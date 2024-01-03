//App.vue

<script setup>
import FromComp from "./components/FormComp.vue";
import Comment from "./components/CommentComp.vue";
</script>

<template>
  <FromComp @formSend="formSend" />
  <button @click="setSortMode('likes')">LIKE</button>
  <button @click="setSortMode('data')">DATA</button>
  <div v-for="(component, index) in comments" :key="index">
    <Comment :value="component.value" :likes="component.likes" :data="component.sec"/>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      comments: [],
      sortMode: "a",
    };
  },
  components: {
    FromComp,
    Comment,
  },
  methods: {
    formSend(value) {
      this.comments.push({
        value: value.comment,
        likes: value.likes,
        sec: value.data,
      });
      console.log(value);
      this.sortedComments();
    },
    setSortMode(button){
      this.sortMode=button=="likes"?'likes':'data';
      this.sortedComments();
    }
    ,
    sortedComments() {
      if (this.sortMode == "likes") {
        this.comments.sort((a, b) => b.likes - a.likes);
      }else{
        this.comments.sort((a, b) => b.sec - a.sec);
      }
    },
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
