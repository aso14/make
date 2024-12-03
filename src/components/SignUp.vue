<template>
  <!-- Sign Up Component -->
  <div
    class="container-fluid min-vh-100 d-flex align-items-center justify-content-center bg-pattern"
  >
    <div class="col-12 col-md-3 p-0 rounded-3 max-width-350">
      <div class="p-4 bg-white rounded-3">
        <h1 class="h5 font-sans fw-semibold text-dark text-center">Sign Up</h1>
        <p class="text-muted text-center">
          Create a new account to get started:
        </p>

        <form>
          <div class="mb-3">
            <input
              type="email"
              class="form-control"
              placeholder="Your Email"
              required
            />
          </div>
          <div class="mb-3">
            <input
              type="password"
              class="form-control"
              placeholder="Your Password"
              required
            />
          </div>
          <div class="mb-3">
            <input
              type="password"
              class="form-control"
              placeholder="Confirm Password"
              required
            />
          </div>
          <div class="form-check mb-3">
            <input
              type="checkbox"
              class="form-check-input"
              id="terms"
              required
            />
            <label class="form-check-label" for="terms">
              I agree to the
              <a href="#" class="text-primary">Terms and Conditions</a>
            </label>
          </div>
          <button class="btn btn-primary w-100 mb-3">Sign Up</button>
          <!-- Google Sign Up Button -->
          <button
            class="btn btn-outline-primary w-100 d-flex align-items-center justify-content-center"
          >
            <img
              src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Google_%22G%22_Logo.svg/512px-Google_%22G%22_Logo.svg.png"
              alt="Google logo"
              width="20"
              height="20"
              class="me-2"
            />
            Sign Up with Google
          </button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SignUpComponent',
};
</script>

<style scoped>
.bg-pattern {
  background-image: url('path/to/whatsapp-pattern.png'); /* Remplace par l'URL de ton motif */
  background-repeat: repeat;
  background-size: contain;
}

.max-width-350 {
  max-width: 350px;
  margin: 0 auto;
}

.form-control {
  border: 1px solid #ced4da;
  border-radius: 0.5rem;
}

.btn-primary {
  background-color: #007bff;
  border-color: #007bff;
}

.btn-outline-primary {
  color: #007bff;
  border-color: #007bff;
}

.btn-outline-primary:hover {
  background-color: #007bff;
  color: #fff;
}
</style>
