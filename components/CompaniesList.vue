<template>
  <div>
    <h3>Trusted by 1,000+ diverse companies</h3>
    <div class="companies">
      <img src="/companies/pipedrive_logo.png" alt="pipedrive_logo" />
      <img src="/companies/seatgeek_logo.png" alt="pipedrive_logo" />
      <img src="/companies/uber_logo.png" alt="pipedrive_logo" />
      <img src="/companies/mention_logo.png" alt="pipedrive_logo" />
      <img src="/companies/birchbox_logo.png" alt="pipedrive_logo" />
    </div>
  </div>
</template>
<style lang="scss" scoped>
h3 {
  font-weight: 400;
  text-transform: uppercase;
  text-align: center;
  font-size: 12px;
  color: $color-grey;
}
.companies {
  width: 100%;
  display: grid;
  grid-gap: 24px;
  grid-template-columns: repeat(5, 1fr);
  margin: 24px auto 64px;
  @include breakpoint(mobileonly) {
    grid-template-columns: 1fr;
  }
  img {
    height: auto;
    max-width: 100%;
    margin: 0 auto;
    @include breakpoint(mobileonly) {
      width: 143px;
    }
  }
}
</style>

