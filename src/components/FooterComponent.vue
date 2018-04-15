<template>
  <footer class="footer">
     <div class="footer__social-wrap">
       <img src="../assets/pool-pros-logo-footer.png" alt="Brand Logo" class="footer__social-logo">
          <div class="footer__social-container">
               <p class="footer__social-text">CONNECT WITH US</p>
               <ul>
                    <router-link to="#" class="footer__social-link" target="_blank">
                         <a href="Twitter">
                              <img src="../assets/twitter-icon.png" alt="Twitter" class="footer__social-icon">
                         </a>
                    </router-link>
                    <router-link to="#" class="footer__social-link" target="_blank">
                         <a href="Facebook">
                              <img src="../assets/facebook-icon.png" alt="Facebook" class="footer__social-icon">
                         </a>
                    </router-link>
                    <router-link to="#" class="footer__social-link" target="_blank">
                         <a href="Youtube">
                              <img src="../assets/youtube-icon.png" alt="Youtube" class="footer__social-icon">
                         </a>
                    </router-link>
               </ul>
          </div>
     </div><!--footer social wrap end-->

     <div class="footer__services-wrap">
          <router-link to="#" class="footer__services-link">Dealers and Distributors</router-link>
          <router-link to="#" class="footer__services-link">Commercial Service</router-link>
     </div><!--footer services wrap end-->

     <div class="footer__menu-wrap">
          <ul class="footer__menu-container">
              <router-link to="#" class="footer__menu-link">
                    <a href="Pool Pros">&copy;2018 Pool Pros</a>
               </router-link> 
               <router-link to="#" class="footer__menu-link">
                    <a href="Privacy Policy">Privacy Policy</a>
               </router-link> 
               <router-link to="#" class="footer__menu-link">
                    <a href="Terms and Conditions">Terms and Conditions</a>
               </router-link> 
          </ul>
     </div><!--footer menu wrap end-->

  </footer><!--footer end-->
</template>

<script>
export default {
     name: 'FooterComponent'
  
}
</script>

<style lang="scss" scoped>
@import '~$scss/main';

     .footer {
          /* FOOTER SOCIAL STYLES */
          &__social-wrap {
               padding: 1.5rem 0;
               background-color: $brand-primary;
               text-align: center;
          }

          &__social-container {
               display: flex;
               justify-content: space-between;
               align-items: center;
               width: 300px;
               margin: 0 auto;

               @include at-breakpoint(md) {
                    justify-content: space-evenly;
               }
          }

          &__social-logo {
               max-width: 200px;
          }

          ul {
               padding-left: 0;
          }

          &__social-text {
               color: $white;
               @extend %sans_bold;
               @include prem(15.23);
          }

          &__social-icon {
               max-width: 20px;
               max-height: 20px;
          }

          /* FOOTER SERVICES MENU STYLES */
          &__services-wrap {
               background-color: $brand-secondary;
               padding: 0.5rem 0;
               text-align: center;
               position: relative;

               @include at-breakpoint(md) {
                    display: none;
               }

               &:after {
                    content: "";
                    height: 1px;
                    width: 320px;
                    left: 0;
                    right: 0;
                    margin: 1rem auto 0 auto;
                    display: block;
                    background-color: $white;
                    border-bottom: 1px white;
               }
          }

          &__services-link {
               color: $white;
               @extend %sans_reg;
               @include prem(11.81);
               padding: 0 0.5rem;

               &:first-child {
                    border-right: 1px solid $white;
               }
          }

          /* FOOTER MENU STYLES */
          &__menu-wrap {
               background-color: $brand-secondary;
               padding: 0.5rem 0;
               text-align: center;
          }

          &__menu-link {
               a {
                    color: $white;
                    @extend %sans_reg;
                    @include prem(12);
                    position: relative;
                    border-right: 1px solid $white;
                    padding: 0 1rem;
               }

               &:last-child {
                    a {
                         border-right: 0;
                    }
               }
          }

     }
</style>
