<template>
  <div>
    <h1>The phone system for modern business</h1>
    <h2>Instant setup. Powerfull integrations. Proven Quality.</h2>
    <form @submit.prevent="submit">
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
        <div class="col-sm-6">
          <label for="inputPhone">Phone Number</label>
          <div class="input-group">
            <div class="input-group-prepend" style="width: 30%;">
              <select name id class="form-control phoneSelect" v-model="countryPhone">
                <option
                  v-for="country in countries"
                  :key="country.name"
                  :value="country.phone"
                >{{country.emoji + ' ' + country.name}}</option>
              </select>
            </div>
            <input
              type="tel"
              class="form-control input-phone"
              :class="{ 'hasError': $v.phone.$error }"
              id="inputPhone"
              v-model="phone"
            />
            <span v-if="countryPhone" class="staticValue">{{'+' + countryPhone}}</span>
          </div>
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
            >{{country.emoji + ' ' + country.name}}</option>
          </select>
        </div>
      </div>
      <input
        type="submit"
        class="btn btn-primary d-block m-auto w-100"
        value="Try Aircall for free"
        :disabled="submitStatus === 'PENDING'"
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
    email: null,
    firstName: null,
    lastName: null,
    phone: null,
    countryPhone: null,
    country: null,
    countries: [],
    submitStatus: null
  }),
  validations: {
    email: {
      required,
      email
    },
    firstName: {
      required
    },
    lastName: {
      required
    },
    phone: {
      required,
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
      if (this.$v.$invalid) {
        this.submitStatus = "ERROR";
      } else {
        // do your submit logic here
        this.submitStatus = "PENDING";
        setTimeout(() => {
          this.$emit("status", "OK");
          this.$emit("mail", this.email);
        }, 500);
      }
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
.input-phone {
  padding-left: 50px;
}
.phoneSelect {
  padding-right: 25px !important;
}
.staticValue {
  position: absolute;
  left: 36%;
  top: 7px;
  z-index: 1020;
}
</style>
