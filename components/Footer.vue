<template>
  <div>
    <nav class="navbar navbar-expand-lg">
      <div class="container">
        <div>
          <ul class="navbar-nav mr-auto">
            <li class="nav-item copyright">©Aircall</li>
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

          <ul class="navbar-nav ml-auto">
            <li class="nav-item mr-2">
              <a href="#">
                <img src="/twitter.svg" alt="aircall-twitter" />
              </a>
            </li>
            <li class="nav-item mr-2">
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
      </div>
    </nav>
  </div>
</template>
<style lang="scss" scoped>
.copyright {
  color: $color-grey;
  font-size: 14px;
  padding: 0.5rem 1rem;
}
.nav-link {
  color: $color-grey;
  font-size: 14px;
  transition: color 0.2s ease-out;
  &:hover {
    color: $color-primary;
  }
}
</style>
