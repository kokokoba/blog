<template>

  <header id="header" class="hero is-medium">
    <div class="hero-head">
      <nav id="navbar" class="navbar has-shadow is-spaced is-transparent">
        <div class="container">
          <div class="navbar-brand">
            <h1 class="title"><nuxt-link to="/" class="nav-item">Tatsuya Engineer Blog</nuxt-link></h1>
            <span class="navbar-burger burger" :class="{ 'is-active': menuActive }"
                  @click="menuToggle()" data-target="navbarMenuHeroA">
              <span></span>
              <span></span>
              <span></span>
            </span>
          </div>

          <div id="navbarMenuHeroA" class="navbar-menu" :class="{ 'is-active': menuActive }">
            <div class="navbar-end">
              <div class="navbar-item">
                <nuxt-link active-class="is-active" to="/" class="navbar-item is-tab" exact>Home</nuxt-link>
                <nuxt-link active-class="is-active" to="/about" class="navbar-item is-tab" exact>About</nuxt-link>
                <nuxt-link active-class="is-active" to="/contact" class="navbar-item is-tab" exact>Contact</nuxt-link>
              </div>
          </div>
        </div>
        </div>
      </nav>
    </div>
  </header>

</template>

<script>
  export default {
    name: "HeaderNav",
    data() {
      return {
        menuActive: false
      }
    }
  }
</script>

<style scoped>
  h1 {
    margin-bottom: 0;
  }

  h1 a {
    color: #333;
    text-decoration: none;
    vertical-align: -webkit-baseline-middle;
  }

</style>
