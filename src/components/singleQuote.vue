<template>
  <div class="quotes">
    <div class="quote">
      <slot ></slot>
    </div>
  </div>
</template>

<script>

</script>

<style lang="scss" scoped>
  .quotes{
    display: inline-block;
  }

  .quote{
    display: flex;
    align-items: center;
    border: 2px dotted red;
    padding: 20px;
    margin: 10px;
    font-family: cursive;
    font-size: 24px;
    width: 315px;
    height: 75px;
    &:hover{
      cursor: pointer;
      background-color: #fa0;
    }
  }
</style>