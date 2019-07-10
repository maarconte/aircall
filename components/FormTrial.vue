<template>
  <div>
    <h1>The phone system for modern business</h1>
    <h2>Instant setup.Powerfull integrations.Proven Quality.</h2>
    <form>
      <div class="row">
        <div class="form-group col-sm-12">
          <label for="inputEmail">Email</label>
          <input
            type="email"
            class="form-control"
            :class="{ 'hasError': $v.email.$error }"
            id="inputEmail"
            v-model="email"
          />
        </div>
        <div class="form-group col-sm-6">
          <label for="inputFirstName">First Name</label>
          <input
            type="text"
            class="form-control"
            :class="{ 'hasError': $v.firstName.$error }"
            id="inputFirstName"
            v-model="firstName"
          />
        </div>
        <div class="form-group col-sm-6">
          <label for="inputLastName">Last Name</label>
          <input
            type="text"
            class="form-control"
            :class="{ 'hasError': $v.lastName.$error }"
            id="inputLastName"
            v-model="lastName"
          />
        </div>
        <div class="form-group col-sm-6">
          <label for="inputPhone">Phone Number</label>
          <input
            type="tel"
            class="form-control"
            :class="{ 'hasError': $v.phone.$error }"
            id="inputPhone"
            v-model="phone"
          />
        </div>
        <div class="form-group col-sm-6">
          <label for="inputCountry">Country</label>
          <select
            class="form-control"
            :class="{ 'hasError': $v.country.$error }"
            id="inputCountry"
            v-model="country"
          >
            <option
              v-for="country in countries"
              :key="country.name"
              :value="country.name"
              v-bind:style="{ 'background': 'url(' + country.file_url + ')' }"
            >{{country.name}}</option>
          </select>
        </div>
      </div>
      <input
        type="submit"
        class="btn btn-primary d-block m-auto w-100"
        value="Try Aircall for free"
      />
    </form>
  </div>
</template>
<script>
import Vue from "vue";
import Vuelidate from "vuelidate";
import { required, email, minLength, numeric } from "vuelidate/lib/validators";
Vue.use(Vuelidate);

export default Vue.extend({
  data: () => ({
    errors: [],
    email: null,
    firstName: null,
    lastName: null,
    phone: null,
    country: null,
    countries: []
  }),
  validations: {
    email: {
      required,
      minLength: minLength(4),
      email
    },
    firstName: {
      required
    },
    lastName: {
      required
    },
    phone: {
      numeric,
      minLength: minLength(4)
    },
    country: {
      required
    }
  },
  methods: {
    submit() {
      this.$v.$touch();
      if (this.$v.$error) return;
    }
  },
  created() {
    fetch("/country-by-flag.json")
      .then(res => res.json())
      .then(res => {
        this.countries = res;
      });
  }
});
</script>

<style lang="scss" scoped>
h2 {
  font-weight: 400;
  font-size: 16px;
}
</style>
