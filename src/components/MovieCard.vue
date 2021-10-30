<template>
    <li>
        <img :src="/poster" alt="">
    </li>
    <li>{{ title }}</li>
    <li>{{ score }}/10</li>
    <li>{{ id }}</li>
</template>

<script>
export default {
  props: {
    poster: {
      type: String,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    score: {
      type: Number,
      required: true
    },
    id: {
      type: Number,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
