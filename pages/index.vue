<template>
  <div>
    <Menu />
    <header>
      <div class="container">
        <div class="wrapper">
          <div class="row">
            <div class="col-sm-5">
              <FormTrial v-if="!submitStatus" v-on:status="updateStatus" v-on:mail="updateMail" />
              <FormTrialSuccess v-if="submitStatus === 'OK'" :mail="mail" />
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
    submitStatus: null,
    mail: null
  }),
  methods: {
    updateStatus(text) {
      this.submitStatus = text;
    },
    updateMail(mail) {
      this.mail = mail;
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