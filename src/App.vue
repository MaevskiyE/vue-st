<template>
    <div class="base">
        <appHeader :counter="quotesCounter" :progress="progress" :maxQuotes="maxQuotes"></appHeader>
        <newQuote :quotes="quotes"></newQuote>
        <quotes :quotes="quotes"></quotes>
    </div>
</template>

<script>
    import Header from './components/header.vue'
    import newQuote from './components/newQuote.vue'
    import Quotes from './components/quotes.vue'
    import { bus } from './main'

    export default {
        data() {
          return {
            quotes: ['This is test quote','This is test quote', 'This is test quote'],
            maxQuotes: 10
          }
        },
        computed: {
          quotesCounter() {
            return this.quotes.length
          },
          progress(){
            return this.quotesCounter + '0'
          }
        },
        components: {
          appHeader: Header,
          newQuote,
          Quotes
        },
        created() {
          bus.$on('deletedQuote', (quote) => {
            this.quotes.splice(quote, 1)
            })
        }
    }
</script>

<style scoped>


</style>