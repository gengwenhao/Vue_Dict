<template>
  <div v-if="isShow" id="translateOutPut" class="ui segment">
    <div>{{ result }}</div>
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
