<template>
  <div class="row">
    <single-quote @click.native='deleteQuote(index)' v-for="(quote, index) in quotes" :key="index"> {{ quote }}</single-quote>
  </div>
</template>

<script>
  import singleQuote from './singleQuote.vue'
  import { bus } from '../main'

  export default {
    props: {
      quotes: {
        type: Array
      }
    },
    created() {
      bus.$on('addedQuote', (quote) => {
        if(this.quotes.length <= 9) {
          this.quotes.push(quote)
        } else {
          alert('Перед добавлением - удалите что-то из старых цитат')
        }
      })
    },
    components: {
      singleQuote
    },
    methods: {
      deleteQuote(index){
        bus.$emit('deletedQuote', index)
      }
    }
  }
</script>

<style>
  .row {
    display: inline-block;
    width: 100%;
  }
</style>
