<template>
  <div class="result">
    <div class="title">{{result[index].title}}</div>
    <div class="desc">{{result[index].desc}}</div>
  </div>
</template>

<script>
export default {
  name: "Result",
  props: ["correctAnswer", "result"],
  computed: {
    index() {
      let index = 0
      this.result.forEach((r, i) => {
        if (this.correctAnswer >= r.min && this.correctAnswer <= r.max)
          index = i
      })
      return index;
    }
  }
}
</script>

<style scoped>

</style>