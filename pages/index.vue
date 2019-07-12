<template>
  <div>
    <Menu />
    <header>
      <div class="container">
        <div class="wrapper">
          <div class="row">
            <div class="col-sm-5">
              <FormTrial v-if="!submitStatus" v-on:send="updateStatus" />
              <FormTrialSuccess v-if="submitStatus === 'OK'" />
            </div>
          </div>
        </div>
      </div>
    </header>
    <div class="container">
      <CompaniesList />
    </div>
    <Footer />
  </div>
</template>

<script>
import Menu from "~/components/Menu.vue";
import FormTrial from "~/components/FormTrial.vue";
import FormTrialSuccess from "~/components/FormTrialSuccess.vue";
import CompaniesList from "~/components/CompaniesList.vue";
import Footer from "~/components/Footer.vue";

export default {
  components: {
    Menu,
    FormTrial,
    FormTrialSuccess,
    CompaniesList,
    Footer
  },
  data: () => ({
    submitStatus: null
  }),
  methods: {
    updateStatus(text) {
      console.log(this.submitStatus);
      this.submitStatus = text;
      console.log(this.submitStatus);
    }
  }
};
</script>
<style lang="scss" scoped>
header {
  background-image: url("/illo@2X.png");
  background-repeat: no-repeat;
  background-size: 70% auto;
  background-position: 100% bottom;
  @include breakpoint(mobileonly) {
    background-image: inherit;
  }
  .wrapper {
    padding-top: 200px;
    padding-bottom: 190px;
  }
}
</style>