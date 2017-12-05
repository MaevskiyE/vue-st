<template>
    <div class="quote">
          <slot></slot>
    </div>
</template>

<script>

</script>

<style lang="scss">
  .quote{
    display: flex;
    flex-direction: column;
    border: 1px solid #67c23a ;
    padding: 10px;
    margin: 5px;
    font-family: cursive;
    font-size: 14px;
    width: 30%;
    /*height: auto;*/
      box-sizing: content-box;

      &-author{
          align-self: flex-end;
      }
    &:hover{
      cursor: pointer;
      background-color: #fa0;
    }
  }
</style>