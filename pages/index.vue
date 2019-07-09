<template>
  <div>
    <Menu />
    <div class="container">
      <FormTrial />
      <PartnersList />
    </div>
    <Footer />
  </div>
</template>

<script>
import Menu from "~/components/Menu.vue";
import FormTrial from "~/components/FormTrial.vue";
import PartnersList from "~/components/PartnersList.vue";
import Footer from "~/components/Footer.vue";

export default {
  components: {
    Menu,
    FormTrial,
    PartnersList,
    Footer
  }
};
</script>
