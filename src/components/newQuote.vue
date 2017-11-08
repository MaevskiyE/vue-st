<template>
  <div class="newQuote">
    <form action="">
      <div class="title">Quote</div>
      <input v-model="newQuote" style="width: 350px; height: 50px; font-size: 16px">
      <button @click.prevent="addNew">Add quote</button>
    </form>
  </div>
</template>

<script>
  import { bus } from '../main'
  export default {
    data() {
      return {
        newQuote: ''
      }
    },
    methods: {
      addNew() {
        let value = this.newQuote.trim();
        if (!value ) {
          return
        }
          bus.$emit('addedQuote', value);
          this.newQuote = '';
      }
    }
  }
</script>

<style scoped>
  .title{
    align-self: flex-start;
    font-size: 24px;
    font-weight: bold;
  }
  .newQuote{
    width: 825px;
    margin: auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  textarea {
    margin-bottom: 25px;
  }
</style>