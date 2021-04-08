<template>
  <div class="about">
    <h1>{{ time }}</h1>

    <div v-if="user">
      {{ user.clientPrincipal.userDetails }} | <a href="/.auth/logout">Logout</a>
    </div>
    <div v-else>
      <a href="/.auth/login/github">Login</a>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      time: null,
      user: null
    }
  },
  async mounted() {
    const response = await fetch("/api/info")
    this.time = await response.text()

    const userResponse = await fetch("/.auth/me")
    if (userResponse.status < 300) {
      this.user = await userResponse.json()
    }
  }
}
</script>