<template>
  <div class="header">
    <div class="title">Quotes Added</div>
    <div class="progress-wrap">
      {{counter}}/{{maxQuotes}}
      <div class="progress" :style="{width: progress + '%'}"></div>
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
      position: relative;
      z-index: 1;
      text-align: center;
      width: 100%;
      height: 25px;
      background-color: #f0f9eb;
      border: 1px solid #c2e7b0;
      .progress{
        position: absolute;
        top: 0;
        z-index: -1;
        width: 10%;
        height: 100%;
        background-color: #67c23a;
        text-align: center;
        transition: .3s;
      }
    }
  }



</style>