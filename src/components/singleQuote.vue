<template>
  <div class="quotes">
    <div class="quote">
      <slot ></slot>
    </div>
  </div>
</template>

<script>

</script>

<style scoped>
  .quotes{
    display: flex;
  }

  .quote{
    border: 2px dotted #ccc;
    padding: 20px;
    margin: 10px;
    font-family: cursive;
    font-size: 24px;
    &:hover{
      cursor: pointer;
      background-color: #fa0;
    }
  }
</style>