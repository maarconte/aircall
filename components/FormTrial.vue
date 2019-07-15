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
            <div class="input-group-prepend">
              <select name id class="form-control" v-model="countryPhone">
                <option
                  v-for="country in countries"
                  :key="country.name"
                  :value="country.phone"
                >{{country.emoji + ' ' + country.name}}</option>
              </select>
            </div>
            <input
              type="tel"
              class="form-control"
              :class="{ 'hasError': $v.phone.$error }"
              id="inputPhone"
              v-model="phone"
            />
            <span v-if="countryPhone" class="input-group-label">{{'+' + countryPhone}}</span>
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
      <button
        type="submit"
        class="d-block m-auto"
        :class="submitStatus === 'PENDING' ? btnAnimation : 'btn btn-primary w-100'"
      ></button>
    </form>
  </div>
</template>
<script>
import Vue from "vue";
import Vuelidate from "vuelidate";
import { required, email, minLength, numeric } from "vuelidate/lib/validators";
import { setTimeout } from "timers";
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
    submitStatus: null,
    btnAnimation: null
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
        this.submitStatus = "PENDING";
        this.btnAnimation = "onclic";
        setTimeout(() => {
          this.btnAnimation = "validate";
        }, 2000);
        setTimeout(() => {
          this.$emit("status", "OK");
          this.$emit("mail", this.email);
        }, 1000);
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
.input-group {
  &-prepend {
    @media (min-width: 375px) {
      width: 16%;
    }
    @media (min-width: 414px) {
      width: 20%;
    }
    @include breakpoint(phablet) {
      width: 30%;
    }

    & select {
      padding-right: 26px !important;
      color: #ffffff;
      @media (max-width: 375px) {
        padding: 0.375rem 0.75rem !important;
      }
    }
  }
  & input {
    padding-left: 55px;
  }
  &-label {
    position: absolute;
    left: 36%;
    top: 7px;
    z-index: 1020;
    @include breakpoint(mobileonly) {
      left: 18%;
    }
  }
}

.btn {
  transition: all 0.25s ease;
  &:after {
    content: "Try Aircall for free";
  }
}

.onclic {
  border-radius: 40px;
  height: 40px;
  width: 40px;
  border-color: #cccccc;
  background: #fff;
  border-width: 3px;
  font-size: 0;
  border-left-color: $color-primary;
  animation: rotating 2s 0.25s linear infinite;
  text-shadow: none;
  outline: none;
  border-style: solid;

  &:after {
    content: "";
  }
}
.validate {
  font-size: 13px;
  color: white;
  background: $color-primary;
  border: none;

  height: 40px;

  width: 40px;

  border-radius: 40px;
  &:after {
    font-family: "FontAwesome";
    content: "\f00c";
  }
}

@keyframes rotating {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>
