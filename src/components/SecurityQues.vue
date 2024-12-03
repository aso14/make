<template>
  <div
    class="container-fluid min-vh-100 d-flex align-items-center justify-content-center bg-white"
  >
    <div class="col-12 col-md-4 p-0 bg-gradient rounded-3 max-width-400">
      <div class="p-4 bg-white rounded-3 bg-pattern">
        <h1 class="h5 font-sans fw-semibold text-dark">Security Question</h1>
        <p class="text-muted">Answer the following question to proceed:</p>

        <form @submit.prevent="handleSubmit">
          <div class="mb-3">
            <select v-model="securityQuestion" class="form-select" required>
              <option disabled value="">Select a security question</option>
              <option>What is your mother's maiden name?</option>
              <option>What was the name of your first pet?</option>
              <option>What is your favorite book?</option>
            </select>
          </div>

          <div class="mb-3">
            <input
              type="text"
              v-model="securityAnswer"
              class="form-control"
              placeholder="Your Answer"
              required
            />
          </div>

          <button class="btn btn-primary w-100" :disabled="loading">
            <span
              v-if="loading"
              class="spinner-border spinner-border-sm"
              role="status"
              aria-hidden="true"
            ></span>
            <span v-else>Verify Answer</span>
          </button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SecurityQuestions',
  data() {
    return {
      securityQuestion: '',
      securityAnswer: '',
      loading: false,
    };
  },
  methods: {
    async handleSubmit() {
      this.loading = true;
      // Simulate API call
      setTimeout(() => {
        if (this.securityAnswer === 'Correct Answer') {
          // Replace with actual verification logic
          this.$emit('submit', { success: true, message: 'Answer verified!' });
        } else {
          this.$emit('submit', {
            success: false,
            message: 'Incorrect answer!',
          });
        }
        this.loading = false;
      }, 2000);
    },
  },
};
</script>

<style scoped>
.bg-pattern {
  background-image: url('path_to_your_pattern_image');
  background-size: cover;
}

.form-select,
.form-control {
  font-family: 'Open Sans', sans-serif; /* Respect the TailwindCSS default font */
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
}

.btn-primary {
  background-color: #3490dc;
  border: none;
}

.max-width-400 {
  max-width: 400px;
  margin: 0 auto;
}
</style>
