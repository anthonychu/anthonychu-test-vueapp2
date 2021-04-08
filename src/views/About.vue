<template>
  <div class="about">
    <h1>{{ time }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      time: null
    }
  },
  async mounted() {
    const response = await fetch("/api/info")
    this.time = await response.text()
  }
}
</script>