<template>
  <div class="footer mt-auto">
    <nav class="navbar navbar-expand-lg">
      <div class="container d-block d-lg-flex">
        <ul class="navbar-nav mr-auto footer_menu">
          <li class="nav-item footer_menu_copyright">©Aircall</li>
          <li class="nav-item">
            <a class="nav-link" href="#">Privacy</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Terms of use</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Site map</a>
          </li>
        </ul>

        <ul class="navbar-nav ml-auto flex-row footer_socials">
          <li class="nav-item">
            <a href="#">
              <img src="/twitter.svg" alt="aircall-twitter" />
            </a>
          </li>
          <li class="nav-item">
            <a href="#">
              <img src="/facebook.svg" alt="aircall-facebook" />
            </a>
          </li>
          <li class="nav-item">
            <a href="#">
              <img src="/linkedin.svg" alt="aircall-linkedin" />
            </a>
          </li>
        </ul>
      </div>
    </nav>
  </div>
</template>
<style lang="scss" scoped>
.footer {
  background-color: $color-grey-lighter;
  border-top: 1px solid $color-grey-light;
  &_menu {
    .nav-link {
      color: $color-grey;
      font-size: 14px;
      transition: color 0.2s ease-out;
      &:hover {
        color: $color-primary;
      }
    }
    &_copyright {
      color: $color-grey;
      font-size: 14px;
      padding: 0.5rem 0;
    }
  }
  &_socials {
    @include breakpoint(mobileonly) {
      margin-top: 16px;
    }
    li:not(:last-child) {
      margin-right: 8px;
      @include breakpoint(mobileonly) {
        margin-right: 16px;
      }
    }
  }
}
</style>
