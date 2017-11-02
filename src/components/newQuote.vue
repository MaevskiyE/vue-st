<template>
  <div class="newQuote">
    <form action="">
      <div class="title">Quote</div>
      <textarea v-model="newQuote" rows='7' cols='100' @keyup.enter="addNew"></textarea>
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
        if(this.newQuote !== '') {
          bus.$emit('addedQuote', this.newQuote);
          this.newQuote = '';
        }
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