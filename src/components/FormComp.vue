// FormComp.vue

<template>
  <form
    @submit.prevent="sendForm"
    style="display: flex; flex-direction: column"
  >
    <label><span>Komentarz: </span><input v-model="data.comment"/></label>
    <label><span>Liczba like: </span><input type="number" v-model="data.likes" /></label>
    <button type="submit">Dodaj komentarz</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      data: {
        comment:"",
        likes:Math.floor(Math.random() * 100) + 1,
        data:0
      },
    };
  },
  methods: {
    sendForm() {
      const today = new Date();
      
      //const hours = today.getHours();
      const minutes = today.getMinutes();
      const seconds = today.getSeconds();

      this.data.data = minutes * 60 + seconds;

      this.$emit("formSend", this.data);
      this.data.likes=Math.floor(Math.random() * 100) + 1;

    },
  },
};
</script>
