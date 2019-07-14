<template>
  <div>
    <nav class="navbar navbar-expand-lg">
      <div class="container">
        <a class="navbar-brand" href="#">
          <img src="/aircall-logo.svg" alt="aircall-logo" />
        </a>
        <span
          class="navbar-toggler btn-menu"
          type="button"
          data-toggle="collapse"
          data-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >Menu</span>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav mr-auto">
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                id="navbarDropdown"
                role="button"
                data-toggle="dropdown"
                aria-haspopup="true"
                aria-expanded="false"
              >Product</a>
              <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                <a class="dropdown-item" href="#">Features</a>
                <a class="dropdown-item" href="#">Apps</a>
              </div>
            </li>
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                id="navbarDropdown"
                role="button"
                data-toggle="dropdown"
                aria-haspopup="true"
                aria-expanded="false"
              >Integration</a>
              <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                <a class="dropdown-item" href="#">Features</a>
                <a class="dropdown-item" href="#">Apps</a>
              </div>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Pricing</a>
            </li>
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                id="navbarDropdown"
                role="button"
                data-toggle="dropdown"
                aria-haspopup="true"
                aria-expanded="false"
              >Partners</a>
              <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                <a class="dropdown-item" href="#">Features</a>
                <a class="dropdown-item" href="#">Apps</a>
              </div>
            </li>
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                id="navbarDropdown"
                role="button"
                data-toggle="dropdown"
                aria-haspopup="true"
                aria-expanded="false"
              >Ressources</a>
              <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                <a class="dropdown-item" href="#">Features</a>
                <a class="dropdown-item" href="#">Apps</a>
              </div>
            </li>
          </ul>
          <div class="ml-auto">
            <ul class="navbar-nav">
              <li class="nav-item">
                <a href="#" class="nav-link">Login</a>
              </li>
              <li class="nav-item">
                <a class="btn btn-outline-primary cta" href="#">Try Aircall for free</a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>

<style lang="scss" scoped>
.cta {
  margin-left: 8px;
}
.btn-menu {
  font-size: 14px;
  font-weight: 600;
  color: $color-primary;
  text-transform: uppercase;
}
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 10;
  @include breakpoint(mobileonly) {
    background-color: #fff;
    box-shadow: 0 1px 1px -1px rgba(16, 24, 32, 0.16);
  }
  .nav-link {
    font-weight: 500;
    color: $color-black;
    transition: color 0.2s ease-out;
    &:hover {
      color: $color-primary;
      &:after {
        background-image: url(/dropdown2.svg);
      }
    }
  }
}
.dropdown-menu {
  background: #fff;
  border-radius: 4px;
  padding: 16px 0;
  box-shadow: 0 0 1px 0 rgba(0, 0, 0, 0.16), 0 24px 24px 0 rgba(0, 0, 0, 0.05),
    0 2px 2px 0 rgba(0, 0, 0, 0.05), 0 4px 4px 0 rgba(0, 0, 0, 0.05),
    0 8px 8px 0 rgba(0, 0, 0, 0.05), 0 16px 16px 0 rgba(0, 0, 0, 0.05);
  @include breakpoint(mobileonly) {
    box-shadow: none;
    border: none;
  }
}
/* Repsonsive */
.navbar-collapse.show {
  padding-top: 10px;
  .nav-item:not(:last-child) {
    border-top: 1px solid $color-grey-lighter;
    padding: 8px 0;
    width: 100%;
  }
  .cta {
    margin: 15px auto;
    display: block;
  }
}
</style>

