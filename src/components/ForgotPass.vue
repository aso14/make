<template>
  <div
    class="container-fluid min-vh-100 d-flex align-items-center justify-content-center bg-pattern"
  >
    <div class="col-12 col-md-3 p-0 rounded-3 max-width-350">
      <div class="p-4 bg-white rounded-3">
        <h1 class="h5 font-sans fw-semibold text-dark text-start">
          Forgot Password
        </h1>
        <p class="text-muted text-start">Select a recovery method:</p>

        <form @submit.prevent="handleSubmit">
          <div class="mb-3">
            <input
              type="email"
              v-model="email"
              class="form-control"
              placeholder="Your Email"
              required
            />
          </div>
          <div class="mb-3">
            <input
              type="text"
              v-model="phone"
              class="form-control"
              placeholder="Your Phone Number (optional)"
            />
          </div>
          <select v-model="method" class="form-select mb-3">
            <option value="email">Email</option>
            <option value="sms">SMS</option>
          </select>
          <button class="btn btn-primary w-100" :disabled="loading">
            <span
              v-if="loading"
              class="spinner-border spinner-border-sm"
              role="status"
              aria-hidden="true"
            ></span>
            <span v-else>Send Reset Link</span>
          </button>
        </form>

        <div v-if="message" class="mt-3 text-center">
          <p class="text-success">{{ message }}</p>
        </div>

        <div v-if="error" class="mt-3 text-center">
          <p class="text-danger">{{ error }}</p>
        </div>

        <div class="text-muted small text-center mt-2">
          <a href="#" class="text-primary">Back to Sign In</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ForgotPasswordComponent',
  data() {
    return {
      email: '',
      phone: '',
      method: 'email',
      loading: false,
      message: '',
      error: '',
    };
  },
  methods: {
    handleSubmit() {
      this.loading = true;
      this.message = '';
      this.error = '';

      // Simulating an API call
      setTimeout(() => {
        if (this.method === 'email' && this.email) {
          this.message = 'Reset link sent to your email!';
        } else if (this.method === 'sms' && this.phone) {
          this.message = 'Reset code sent to your phone!';
        } else {
          this.error = 'Please enter a valid input!';
        }
        this.loading = false;
      }, 2000);
    },
  },
};
</script>

<style scoped>
.bg-pattern {
  background-image: url('/path/to/your/pattern.png');
  background-size: cover;
}
</style>
