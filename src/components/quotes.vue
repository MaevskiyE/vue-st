<template>
  <div class="quotes">
    <single-quote @click.native='deleteQuote(index)' v-for="(quote, index) in quotes" :key="index">
      <div class="quote-body">
        {{ quote.quote }}
      </div>
      <span class="quote-author">
        {{quote.author}}
      </span>
    </single-quote>
  </div>
</template>

<script>
  import singleQuote from './singleQuote.vue'
  import { bus } from '../main'

  export default {
    data: function() {
      return{
        message: ''
      }
    },
    props: {
      quotes: {
        type: Array
      }
    },
    created() {
      bus.$on('addedQuote', (quote) => {
        if(this.quotes.length < 10) {
          this.quotes.push(quote)
          this.success()
        } else {
          this.error()
        }
      })
    },
    components: {
      singleQuote
    },
    methods: {
      deleteQuote(index){
        bus.$emit('deletedQuote', index)
      },
      error() {
        this.$message({
          showClose: true,
          message: 'You should delete quote before adding new one',
          type: 'warning'
        })
      },
      success() {
        this.$message({
          showClose: true,
          message: 'Your quote is successfully added',
          type: 'success'
        })
      },
    }
  }
</script>

<style lang="scss">
  .quotes{
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    flex-wrap: wrap;
  }
</style>
