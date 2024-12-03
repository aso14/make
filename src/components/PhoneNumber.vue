<template>
  <div
    class="container-fluid min-vh-100 d-flex align-items-center justify-content-center bg-white"
  >
    <div class="col-12 col-md-4 p-0 bg-gradient rounded-3 max-width-400">
      <div class="p-4 bg-white rounded-3">
        <h1 class="h5 font-sans fw-semibold text-dark text-start">
          Add Your Phone Number
        </h1>
        <p class="text-muted text-start">
          Please enter your phone number along with the country code.
        </p>

        <div class="mb-3 d-flex align-items-center">
          <select v-model="selectedCountry" class="form-select me-2">
            <option
              v-for="country in countries"
              :key="country.code"
              :value="country.code"
            >
              <img :src="country.flag" alt="" class="country-flag" />
              {{ country.name }} (+{{ country.code }})
            </option>
          </select>

          <input
            type="text"
            v-model="phoneNumber"
            placeholder="Your Phone Number"
            class="form-control w-100"
          />
        </div>

        <div class="text-center">
          <button @click="addPhoneNumber" class="btn btn-primary w-100 mt-3">
            Add Phone Number
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PhoneNumberInput',
  data() {
    return {
      selectedCountry: '',
      phoneNumber: '',
      countries: [
        {
          name: 'United States',
          code: '1',
          flag: 'https://restcountries.com/v3.1/flags/us.svg',
        },
        {
          name: 'Canada',
          code: '1',
          flag: 'https://restcountries.com/v3.1/flags/ca.svg',
        },
        {
          name: 'France',
          code: '33',
          flag: 'https://restcountries.com/v3.1/flags/fr.svg',
        },
        {
          name: 'Germany',
          code: '49',
          flag: 'https://restcountries.com/v3.1/flags/de.svg',
        },
        {
          name: 'United Kingdom',
          code: '44',
          flag: 'https://restcountries.com/v3.1/flags/gb.svg',
        },
        // Add more countries as needed
      ],
    };
  },
  methods: {
    addPhoneNumber() {
      if (this.phoneNumber && this.selectedCountry) {
        alert(`Phone Number: +${this.selectedCountry} ${this.phoneNumber}`);
        // Add your logic to handle the phone number here
      } else {
        alert('Please enter a valid phone number.');
      }
    },
  },
};
</script>

<style scoped>
.country-flag {
  width: 20px; /* Adjust flag size as needed */
  height: auto; /* Maintain aspect ratio */
  margin-right: 5px;
}
</style>
