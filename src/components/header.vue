<template>
  <div class="header">
    <div class="title">Quotes Added</div>
    <div class="progress-wrap">
      <div class="progress" :style="{width: progress + '%'}">{{counter}}/10</div>
    </div>
  </div>
</template>

<script>
  import { bus } from '../main'
  export default {
    props: {
      counter: {
        type: Number
      },
      progress: {
        type: String
      }
    },
    data() {
      return {
      }
    },
    created() {
      bus.$on('progress', (info) => {
        this.info = info;
      })
    }
  }
</script>

<style scoped>
  .header{
    width: 1170px;
    margin: 100px auto;
  }
  .title{
    font-size: 36px;
    font-weight: bold;
  }
  .progress-wrap{
    width: 100%;
    height: 25px;
    background-color: #ccc;
  }
  .progress{
    width: 10%;
    height: 100%;
    background-color: red;
    text-align: center;
  }
</style>