<template>
  <div class="hello">
    <h1 v-if="displayed">{{ title }}</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    displayed: Boolean
  },
  data () {
    return {
      title: 'Web Avatar'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
