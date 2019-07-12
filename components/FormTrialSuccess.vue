<template>
  <div class="card">
    <h1>
      Hey, we've sent you an email to
      <span>{{mail}}</span>
    </h1>
    <p>Please confirm your account by following the steps provided in the email.</p>
    <a class="btn btn-primary" href="https://aircall.io">Back to homepage</a>
  </div>
</template>

<script>
import Vue from "vue";
export default Vue.extend({
  props: ["mail"]
});
</script>


<style lang="scss" scoped>
.card {
  padding: 80px 30px;
  display: block;
}
span {
  color: $color-primary;
}
</style>

