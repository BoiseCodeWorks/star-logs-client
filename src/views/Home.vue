<template>
  <div class="home">
    
  </div>
</template>

<script>
export default {
  name: "home",
  mounted() {
    if (!this.$store.state.user._id) {
      this.$router.push({ name: "login" });
    }
  }
};
</script>
