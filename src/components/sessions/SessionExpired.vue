<template>
  <div
    class="container-fluid min-vh-100 d-flex align-items-center justify-content-center bg-white"
  >
    <div class="col-12 col-md-4 p-0 bg-gradient rounded-3 max-width-400">
      <div class="p-4 bg-white rounded-3 bg-pattern">
        <h1 class="h5 font-sans fw-semibold text-dark">Session Expired</h1>
        <p class="text-muted">
          Your session has expired. Please log in again to continue.
        </p>

        <button class="btn btn-primary w-100 mt-3" @click="logInAgain">
          Log In Again
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SessionExpiredError',
  methods: {
    logInAgain() {
      // Logic to redirect the user to login page
      this.$emit('logInAgain');
    },
  },
};
</script>

<style scoped>
.bg-pattern {
  background-image: url('path_to_your_pattern_image');
  background-size: cover;
}

.max-width-400 {
  max-width: 400px;
  margin: 0 auto;
}

.text-primary {
  color: #3490dc;
  cursor: pointer;
}

.text-muted {
  color: #6c757d;
}
</style>
