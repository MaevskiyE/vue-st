<template>
  <div class="container">
    <div class="newQuote">
      <form>
        <div class="title">Your quote:</div>
        <textarea v-model="newQuote"></textarea>
      </form>
      <el-button @click.prevent="addNew" type="success" plain>Add new quote</el-button>
      <el-button @click.prevent="addRandom" type="success" plain>Add random quote</el-button>
    </div>
    <div class="legend">Legend:
      <p>"Add new quote" - add to store your quote from textarea</p>
      <p>"Add random quote" - generate random quote to store</p>
      <p>By pressing on already created quote - you will delete it</p>
    </div>
  </div>
</template>

<script>
  import { bus } from '../main'
  import axios from 'axios'

  export default {
    data() {
      return {
        newQuote: '',
        randomQuote: []
      }
    },
    methods: {
      addNew() {
        if(!this.newQuote.trim()) {
          return
        }
        let value = {
          quote: this.newQuote,
          author: ''
        }
          bus.$emit('addedQuote', value);
          this.newQuote = '';
      },
      addRandom(){
        axios.get(`https://random-quote-generator.herokuapp.com/api/quotes/random`)
          .then(response => {
            // JSON responses are automatically parsed.

            this.randomQuote = response.data
            let value = this.randomQuote;
            if (!value ) {
              return
            }
            bus.$emit('addedQuote', value);
            this.newQuote = '';
          })
      }
    }
  }
</script>

<style lang="scss" scoped>
  .title{
    align-self: flex-start;
    font-size: 24px;
    font-weight: bold;
  }
  .container{
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 25px;
  }
  .newQuote{

    textarea{
      width: 355px;
      height: 70px;
      font-size: 16px;
      margin-bottom: 10px;
    }
  }
  .legend{
    font-size: 16px;
    font-weight: bold;
    p{
      margin: 5px 0;
      /*font-size: 16px;*/
      font-weight: normal;
    }
  }
</style>