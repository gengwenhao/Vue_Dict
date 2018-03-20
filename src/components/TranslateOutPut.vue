<template>
  <div v-show="isShow" id="translateOutPut" class="ui segment">
    <span>查词结果: {{ result }}</span>
  </div>
</template>

<script>
  export default {
    name: 'translate-output',
    props: [
      'result',
      'isShow'
    ]
  }
</script>

<style scoped>

</style>
