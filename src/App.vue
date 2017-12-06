<template>
    <div class="container">
        <appHeader :counter="quotesCounter" :progress="progress" :maxQuotes="maxQuotes"></appHeader>
        <newQuote :quotes="quotes"></newQuote>
        <quotes :quotes="quotes"></quotes>
    </div>
</template>

<script>
    export default {
        data() {
          return {
            quotes: [],
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

<style lang="scss">
    body{
        background-color: #eeeeee;
    }
    .container{
        width: 960px;
        margin: 0 auto;
    }

</style>