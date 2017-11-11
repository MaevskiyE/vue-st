<template>
    <div class="container">
        <p v-highlight:backgroundColor.delayed.blink="{mainColor: 'yellow', secondColor: 'brown', delay: 500}">Some text</p>
    </div>
</template>

<script>
  export default {
    directives: {
      'highlight': {
        bind(el, binding, vnode) {
          let delay = 0
          if (binding.modifiers['delayed']) {
            delay = 3000;
          }
          if (binding.modifiers['blink']) {
            let mainColor = binding.value.mainColor;
            let secondColor = binding.value.secondColor;
            let currentColor = mainColor;
            setTimeout(() => {
              setInterval(() => {
                currentColor == secondColor ? currentColor = mainColor : currentColor = secondColor;
                if (binding.arg == 'backgroundColor') {
                  el.style.backgroundColor = currentColor
                } else {
                  el.style.color = currentColor
                }
              }, binding.value.delay)
            }, delay)
          }
        }
      }
    }
  }
</script>

<style scoped>


</style>