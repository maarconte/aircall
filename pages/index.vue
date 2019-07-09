<template>
  <div>
    <Menu />
    <header>
      <div class="container">
        <div class="wrapper">
          <FormTrial />
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
import CompaniesList from "~/components/CompaniesList.vue";
import Footer from "~/components/Footer.vue";

export default {
  components: {
    Menu,
    FormTrial,
    CompaniesList,
    Footer
  }
};
</script>
<style lang="scss" scoped>
header {
  min-height: 700px;
  background-image: url("/illo@2X.png");
  background-repeat: no-repeat;
  background-size: 70% auto;
  background-position: 100% bottom;
  @include breakpoint(mobileonly) {
    background-image: inherit;
    min-height: inherit;
  }
  .wrapper {
    padding-top: 200px;
    padding-bottom: 190px;
  }
}
</style>