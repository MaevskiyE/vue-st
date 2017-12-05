<template>
  <div class="header">
    <div class="title">Quotes Added</div>
    <div class="progress-wrap">
      <div class="progress" :style="{width: progress + '%'}">{{counter}}/{{maxQuotes}}</div>
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
      maxQuotes: {
        type: Number
      },
      progress: {
        type: String
      }
    }
  }
</script>

<style lang="scss" scoped>
  .header{
    width: 100%;
    margin: 30px auto;
    .title{
      font-size: 24px;
      font-weight: bold;
      margin-bottom: 15px;
    }
    .progress-wrap{
      width: 100%;
      margin: 0 5px;
      height: 25px;
      background-color: #f0f9eb;
      border: 1px solid #c2e7b0;
      .progress{
        width: 10%;
        height: 100%;
        background-color: #67c23a;
        text-align: center;
        transition: .3s;
      }
    }
  }



</style>