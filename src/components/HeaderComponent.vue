<template>
  <header>
    <div class="services" role="services bar">
      <div class="container">
        <div class="services__wrap">
          <a href="" class="services__link">Dealers and Distributors</a>
          <a href="" class="services__link">Commercial Service</a>
        </div>
      </div>
    </div><!--services bar end-->
    <div class="navbar">
        <div class="container navbar__container">
          <div class="navbar__wrap">
            <a href="/" class="navbar__logo">
              <img src="../assets/pool-pros-logo.png" alt="Brand Logo" class="navbar__logo-img">
            </a>

            <a href="/" class="navbar__link navbar__button navbar__mobile-button" >
              <img src="../assets/location-icon.png" alt="Location Icon" class="navbar__icon"> Find a Pro
            </a>

            <button class="navbar__toggle" v-on:click="toggleNav" v-bind:class="{ active: isActive }">
              <img src="../assets/menu-icon-mobile.png">
            </button>

            <nav class="navbar__nav" v-bind:class="{ active: isActive }">
              <ul>
                <p class="navbar__menu-text">MENU</p>
                <router-link to="#" class="navbar__link navbar__icon-arrow">Pool & Spas</router-link>
                <router-link to="#" class="navbar__link navbar__icon-arrow">Supplies</router-link>
                <router-link to="#" class="navbar__link navbar__icon-arrow">Resources</router-link>
                <router-link to="#" class="navbar__link navbar__icon-arrow">Services</router-link>
                <router-link to="#" class="navbar__link navbar__button navbar__desktop-button">
                  <img src="../assets/location-icon.png" alt="Location Icon" class="navbar__icon"> Find a Pool Pro
                </router-link>
              </ul>
            </nav><!--navigation end-->
          </div><!--navbar wrap end-->
        </div><!--container end-->
      </div><!--navbar end-->
  </header>
</template>

<script>
export default {
  name: 'HeaderComponent',
  data () {
    return {
      isActive: false
    }
  },
  methods: {
   toggleNav: function() {
     this.isActive = !this.isActive;
   }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '~$scss/main';

/* SERVICE BAR STYLES */
.services {
  background-color: $brand-primary;
  padding: 0.75rem 0;
  display: none;

  @include at-breakpoint(md) {
    display: block;
  }

  &__wrap {
    display: flex;
    justify-content: flex-end;
  }

  &__link {
    color: $white;
    @extend %sans_reg;
    @include prem(12);
    margin-right: 3.5rem;
  }
}

/* NAVIGATION BAR STYLES */
.navbar {
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.16), 0 2px 10px rgba(0, 0, 0, 0.12);
  min-height: 75px;
  padding: 1.5rem 0 0 0;

  @include at-breakpoint(md) {
    padding: 1.9rem 0;
    min-height: 100px;
  }

  &__container {
    max-width: 100%;

    @include at-breakpoint(md) {
      max-width: 90%;
    }
  }

  &__wrap {
    
    @include at-breakpoint(md) {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
  }

  &__logo {
    display: inline-block;
    vertical-align: middle;
    padding-left: 1rem;
    outline: none;

    @include at-breakpoint(md) {
      display: block;
      padding-left: 0;
    }
  }

  &__logo-img {
    max-width: 150px;

    @include at-breakpoint(lg) {
      max-width: 240px;
    }
  }

  &__nav {
    position:absolute;
    cursor:pointer;
    top: -100%;

    @include at-breakpoint(md) {
      width: 75%;
      position: relative;
      left: 0;
      top: 0;
    }

    @include at-breakpoint(lg) {
      width: 57%;
    }

    ul {
      padding: 0;
      margin-top: 1rem;
      border-top: 5px solid $btn-primary;
      border-bottom: 5px solid $btn-primary; 

      @include at-breakpoint(md) {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-top: 0;
        border-top: 0;
        border-bottom: 0;
      }
    }

    &.active {
      display: block;
      position: relative;
      overflow-y: hidden;
    }
  }

  &__menu-text {
    text-align: center;
    @include prem(18);
    color: $brand-primary;
    @extend %sans_bold;

    @include at-breakpoint(md) {
      display: none;
    }
  }

  &__link {
    @include prem(15);
    @extend %sans_bold;
    color: $brand-primary;
    display: block;
    padding: 1rem 0 1rem 1rem;
    background-color: $gray;
    border-bottom: 2px solid $white;

    @include at-breakpoint(md) {
      padding: 0;
      background-color: $white;
      border-bottom: 0;
    }
  }

  &__icon-arrow {
    position: relative;

    &:after {
      content: "";
      position: absolute;
      width: 50px;
      height: 50px;
      background-image: url("../assets/next-arrow.png");
      background-repeat: no-repeat;
      right: 10px;
      top: 10px;
    }

    @include at-breakpoint(md) {
      &:after {
        display: none;
      }
    }
  }

  &__button {
    border: 1px solid $brand-secondary;
    border-radius: 3px;
    padding: 0.7rem 1rem;

    img {
      max-width: 12px;
      display: inline-block;
      vertical-align: middle;
    }
  }

  &__mobile-button {
    display: inline-block;
    margin-left: 1rem;
    padding: 0.5rem 1rem;

    @include at-breakpoint(md) {
      display: none;
    }
  }

  &__desktop-button {
    display: none;

    @include at-breakpoint(md) {
      display: block;
    }
  }

  &__toggle {
    display: inline-block;
    max-width: 60px;
    position: absolute;
    right: 20px;
    top: 20px;
    border: 0;
    outline: none;

    @include at-breakpoint(md) {
      display: none;
    }
  }
}

</style>
