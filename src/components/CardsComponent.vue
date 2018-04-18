<template>
  <div class="cards container">
     <div class="card" v-for="dealer in filteredDealers" :key="dealer.data.id">
        <h2 class="cards__heading">{{ dealer.data.name }}</h2>
        <div class="cards__wrap-phone">
          <img src="../assets/phone-icon-desktop.png" alt="Phone Icon Desktop" class="phone-icon desktop">
          <img src="../assets/phone-icon-mobile.png" alt="Phone Icon Mobile" class="phone-icon mobile">
          <p class="cards__text-number">{{ dealer.data.phone1 }}</p>
        </div>
        <span>Can't talk now? Click below to send an email.</span>
        <button class="cards__button-contact">
            <img src="../assets/email-icon.png" alt="Email Icon" class="cards__img-contact">
            <p class="cards__button-text">Contact this Pro</p>
        </button>
        <p class="cards__text-hours">Business Hours</p>
        <ul class="cards__text-time">
          <li v-if="dealer.data.weekHours.mon">
            Weekdays: {{ dealer.data.weekHours.mon }}
          </li>
          <li>
            Saturdays: {{ dealer.data.weekHours.sat }}
          </li>
          <li>
            Sundays: {{ dealer.data.weekHours.sun }}
          </li>
        </ul>
        <ul class="cards__certifications">
          <li v-if="dealer.data.certifications[0]">
              <img src="../assets/star-installation-pro.png" alt="Certification Icon" class="cards__certification-icon">
              {{ dealer.data.certifications[0] }}
          </li>
          <li v-if="dealer.data.certifications[1]">
              <img src="../assets/gear-service-pro.png" alt="Certification Icon" class="cards__certification-icon">
              {{ dealer.data.certifications[1] }}
          </li>
          <li v-if="dealer.data.certifications[2]">
              <img src="../assets/home-residential-pro.png" alt="Certification Icon" class="cards__certification-icon">
              {{ dealer.data.certifications[2] }}
          </li>
          <li v-if="dealer.data.certifications[3]">
              <img src="../assets/users-commercial-pro.png" alt="Certification Icon" class="cards__certification-icon">
              {{ dealer.data.certifications[3] }}
          </li>       
        </ul>
     </div>
   </div><!--cards end-->
</template>

<script>
import axios from 'axios';
import { EventBus } from '../event-bus.js';

export default {
  name: 'CardsComponent',
  created(){
    const vm = this;
    EventBus.$on('filterChange', ({filter}) => {
      console.log(`FilterChange event caught in CardsComponent:`, filter);
      vm.activeFilter = filter;
    });
  },
  data() {
       return {
            activeFilter: false,
            dealers: []
       }
  },
  mounted() {
       axios.get('../../static/json/dealers.json')
       .then(response => {
        this.dealers = response.data.dealers
        // console.log(response.data);
      })
      .catch(err => {
        console.log(err);
      })
  },
  computed: {
    filteredDealers() {
        const vm = this;
        return vm.dealers.filter((dealer) => {
          let newDealer = dealer.data;
          // console.log(newDealer);
          if(vm.activeFilter){
            console.log('filter is active');
            if(newDealer.certifications && newDealer.certifications.includes(vm.activeFilter)) return newDealer;
          } else {
            return newDealer;
          }
        }); // return resulting array
    }
  }
}

</script>

<style lang="scss" scoped>
@import '~$scss/main';

.cards {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  flex-grow: 4;
  padding: 1rem 0;

  .card {
    width: 100%;
    border-radius: 10px;
    padding: 1rem 0 0 0;
    margin: 0 0.5rem 2rem 0.5rem;
    -webkit-box-shadow: 0px 3px 6px 1px rgba(206,206,206,1);
    -moz-box-shadow: 0px 3px 6px 1px rgba(206,206,206,1);
    box-shadow: 0px 3px 6px 1px rgba(206,206,206,1);

    @include at-breakpoint(md) {
      width: 32%;
    }
  }

  &__heading {
    @extend %sans_light;
    @include prem(26);
    text-align: center;
    border-bottom: 2px solid $gray;
    height: 90px;
    margin: 1rem;
  }

  &__wrap-phone {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 80%;
    margin: 0 auto 1rem auto;
    background-color: $brand-secondary;
    border-radius: 4px;
    height: 45px;

    @include at-breakpoint(sm) {
      margin: 0;
      width: 100%;
      background-color: transparent;
    }

    @include at-breakpoint(md) {
      
    }
  }

  .phone-icon {
    width: 25px;
    height: 25px;
    margin-right: 1rem;

    &.mobile {

      @include at-breakpoint(sm) {
        display: none;
      }
    }

    &.desktop {
      display: none;

      @include at-breakpoint(sm) {
        display: inline-block;
      }
    }
  }

  &__text-number {
    @extend %sans_bold;
    @include prem(26.19);
    margin: 1rem 0;
    color: $white;

    @include at-breakpoint(sm) {
      color: $text-primary;
    }
  }

  span {
    display: block;
    text-align: center;
    @extend %sans_ital;
    @include prem(12);
  }

  &__button-contact {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 2rem auto;
    border: 1px solid $btn-primary;
    padding: 0 1.5rem;
    border-radius: 3px;
    @extend %sans_bold;
    @include prem(15);
    color: $brand-primary;
  }

  &__img-contact {
    max-width: 15px;
    margin-right: 1rem;
  }

  &__text-hours {
    text-align: center;
    @extend %sans_bold;
    @include prem(14);
    margin-bottom: 0.5rem;
  }

  &__text-time {
    padding: 0;
    display: block;
    text-align: center;
    margin-bottom: 2rem;
    @extend %sans_reg;
    @include prem(13);
  }

  &__certifications {
    display: flex;
    justify-content: flex-start;
    flex-wrap: wrap;
    flex-grow: 6;
    background-color: $gray;
    padding: 2rem;

    li {
      width: 49%;
      margin-bottom: 1rem;
      padding-left: 0.5rem;
      display: flex;
      align-items: center;
      @extend %sans_reg;
      @include prem(12);
    }
  }

  &__certification-icon {
    max-width: 15px;
    margin-right: 0.5rem;
  }

}

</style>


