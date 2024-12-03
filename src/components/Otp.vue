<template>
  <div
    class="container-fluid min-vh-100 d-flex align-items-center justify-content-center bg-white"
  >
    <div class="col-12 col-md-4 p-0 bg-gradient rounded-3 max-width-400">
      <div class="p-4 bg-white rounded-3 bg-pattern">
        <h1 class="h5 font-sans fw-semibold text-dark">OTP Verification</h1>
        <p class="text-muted">Enter the 8-digit OTP sent to you:</p>

        <form @submit.prevent="submitOTP">
          <div class="d-flex justify-content-between mb-3">
            <input
              v-model="otp[0]"
              type="text"
              class="form-control otp-input"
              maxlength="1"
            />
            <input
              v-model="otp[1]"
              type="text"
              class="form-control otp-input"
              maxlength="1"
            />
            <input
              v-model="otp[2]"
              type="text"
              class="form-control otp-input"
              maxlength="1"
            />
            <input
              v-model="otp[3]"
              type="text"
              class="form-control otp-input"
              maxlength="1"
            />
            <input
              v-model="otp[4]"
              type="text"
              class="form-control otp-input"
              maxlength="1"
            />
            <input
              v-model="otp[5]"
              type="text"
              class="form-control otp-input"
              maxlength="1"
            />
            <input
              v-model="otp[6]"
              type="text"
              class="form-control otp-input"
              maxlength="1"
            />
            <input
              v-model="otp[7]"
              type="text"
              class="form-control otp-input"
              maxlength="1"
            />
          </div>
          <button class="btn btn-primary w-100">Verify</button>
        </form>

        <p class="mt-3 text-muted">
          Didn't receive the OTP?
          <a href="#" class="text-primary" @click.prevent="resendOTP"
            >Resend OTP</a
          >
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'OTPVerification',
  data() {
    return {
      otp: ['', '', '', '', '', '', '', ''],
    };
  },
  methods: {
    submitOTP() {
      // Logic for submitting OTP
      console.log(this.otp.join(''));
    },
    resendOTP() {
      // Logic to resend OTP
      console.log('Resending OTP...');
    },
  },
};
</script>

<style scoped>
.bg-pattern {
  background-image: url('path_to_your_pattern_image');
  background-size: cover;
}

.otp-input {
  width: 40px;
  height: 40px;
  text-align: center;
  font-size: 1.5rem;
  margin-right: 8px;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
}
</style>
