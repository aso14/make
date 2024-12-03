<template>
  <div
    class="container-fluid min-vh-100 d-flex align-items-center justify-content-center bg-white"
  >
    <div class="col-12 col-md-4 p-0 bg-gradient rounded-3 max-width-400">
      <div class="p-4 bg-white rounded-3 bg-pattern">
        <h1 class="h5 font-sans fw-semibold text-dark">
          Authentication Failed
        </h1>
        <p class="text-muted">
          We were unable to authenticate your identity. Please try again or
          contact support for help.
        </p>

        <button class="btn btn-primary w-100 mt-3" @click="retryAuthentication">
          Retry Authentication
        </button>

        <div class="mt-3 small text-center">
          <a href="#" class="text-primary" @click="contactSupport"
            >Contact Support</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AuthFailed',
  methods: {
    retryAuthentication() {
      // Add logic to retry authentication
      this.$emit('retry');
    },
    contactSupport() {
      // Logic for contacting support
      this.$emit('contactSupport');
    },
  },
};
</script>

<style scoped>
.bg-pattern {
  background-image: url('path_to_your_pattern_image');
  background-size: cover;
}

.btn-primary {
  background-color: #3490dc;
  border: none;
}

.max-width-400 {
  max-width: 400px;
  margin: 0 auto;
}

.text-primary {
  color: #3490dc;
  cursor: pointer;
}
</style>
