<template>
  <!-- Sign In Component -->
  <div
    class="container-fluid min-vh-100 d-flex align-items-center justify-content-center bg-pattern"
  >
    <div class="col-12 col-md-3 p-0 rounded-3 max-width-350">
      <div class="p-4 rounded-3">
        <h1 class="h5 font-sans fw-semibold text-dark text-start">Sign In</h1>
        <p class="text-muted text-start">Log in to your account:</p>

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
            <input type="checkbox" class="form-check-input" id="rememberMe" />
            <label class="form-check-label" for="rememberMe">
              Remember Me
            </label>
          </div>
          <button class="btn btn-primary w-100">Sign In</button>
          <div class="text-muted small text-center mt-2">
            <a href="/ForgotPass" class="text-primary">Forgot Password?</a>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SignInComponent',
};
</script>
