<template>
  <div class="filter">
       <div class="filter__wrap">
            <div class="filter__text-wrap">
                 <p class="filter__dealers">7 Dealers in 28226</p>
                 <p class="filter__filter-text">Filter Results</p>
                 <div class="filter__caret-wrap">
                      <img src="../assets/caret.png" class="filer__caret" alt="Down Caret">
                 </div>
            </div>
            <div class="filter__mobile-wrap">
               <div class="filter__input-wrap">
                    <input type="checkbox" class="filter__checkbox" id="checkbox-1" name="checkbox-1" value="service">
                    <label class="filter__label" for="checkbox-1">Service</label>
               </div>
               <div class="filter__input-wrap">
                    <input type="checkbox" class="filter__checkbox" id="checkbox-2" name="checkbox-2" value="installation">
                    <label class="filter__label" for="checkbox-2">Installation</label>
               </div>
               <div class="filter__input-wrap">
                    <input type="checkbox" class="filter__checkbox" id="checkbox-3" name="checkbox-3" value="residential">
                    <label class="filter__label" for="checkbox-3">Residential</label>
               </div>
               <div class="filter__input-wrap">
                    <input type="checkbox" class="filter__checkbox" id="checkbox-4" name="checkbox-4" value="commerical">
                    <label class="filter__label" for="checkbox-4">Commercial</label>
                    <button class="filter__tool-tip" v-tooltip="'Please click a filter button'">
                         <img src="../assets/tool-tip-icon-filtering.png" alt="Tool Tip">
                    </button>
               </div>
            </div>
       </div>
  </div>
</template>

<script>
export default {
  
}
</script>

<style lang="scss" scoped>
@import '~$scss/main';

.filter {
     background-color: $gray;
     border-radius: 6px;

     @include at-breakpoint(md) {
          width: 90%;
          margin: 0 auto;
          padding: 0;
     }

     &__wrap {
          padding: 1rem 0;

          @include at-breakpoint(md) {
               display: flex;
               align-items: center;
               justify-content: space-evenly;
               width: 85%;
               margin: auto;
               padding: 0;
          }
     }

     &__mobile-wrap {
          display: flex;
          align-items: flex-start;
          flex-direction: column;
          margin: 0 1rem;
          padding: 1rem;
          background-color: $white;
          border: 1px solid $border;

          @include at-breakpoint(md) {
               flex-direction: row;
               align-items: center;
               padding: 0;
               margin: 0;
               background-color: $gray;
               border: 0;
          }
     }

     &__text-wrap {
          display: flex;
          justify-content: flex-start;

          @include at-breakpoint(md) {
               justify-content: space-evenly;
          }
          
     }

     &__caret-wrap {
          margin-top: 1.1rem;
          padding: 1.5rem 0.7rem 0 0.8rem;
          border-top: 1px solid $border;
          border-right: 1px solid $border;

          @include at-breakpoint(md) {
               display: none;
          }
     }

     &__dealers {
          @extend %sans_bold;
          color: $brand-secondary;
          @include prem(17.97);
          padding: 1rem;
          margin-bottom: 0;

          @include at-breakpoint(md) {
               margin: 1rem 0;
          }

          @include at-breakpoint(xl) {
               margin-right: 5rem;
          }
     }

     &__filter-text {
          @extend %sans_bold;
          color: $text-primary;
          @include prem(17.97);
          padding: 1rem;
          background-color: $white;
          border-top: 1px solid $border;
          border-left: 1px solid $border;
          border-right: 1px solid $border;
          margin-bottom: 0;
          
          @include at-breakpoint(md) {
               background-color: $gray;
               border-top: 0;
               border-left: 0;
               border-right: 0;
               margin: 1rem 0;
          }
     }

     &__input-wrap:last-child {
          display: flex;
     }

     &__checkbox {
        opacity: 0;
        position: absolute;
    }

    &__checkbox,
    &__label {
        display: inline-block;
        vertical-align: middle;
        margin: 5px;
        cursor: pointer;
    }

    &__label {
        position: relative;
        @extend %sans_reg;
        @include prem(16);
        margin-left: 0.5rem;

        @include at-breakpoint(md) {
             @include prem(11.98);
        }
    }

    &__checkbox + &__label:before {
        content: '';
        background: #fff;
        border: 5px solid $brand-secondary;
        border-radius: 5px;
        display: inline-block;
        vertical-align: middle;
        width: 10px;
        height: 10px;
        padding: 2px;
        margin-right: 10px;
        text-align: center;
    }

    &__checkbox:checked + &__label:before {
        background: $brand-secondary;
        box-shadow: inset 0px 0px 0px 4px #fff;
    }

     &__tool-tip {
          border: 0;
          outline: none;
          background-color: $gray;
          img {
               max-width: 25px;
               display: inline-block;
               vertical-align: middle;
          }
     }
}
</style>

