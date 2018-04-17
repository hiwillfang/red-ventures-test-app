<template>
  <div class="container">
       <div class="filter">
       <div class="filter__wrap">
            <p class="filter__dealers">7 Dealers in 28226</p>
            <p class="filter__filter-text">Filter Results</p>
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
     padding: 1rem 0;
     border-radius: 6px;

     &__wrap {
          display: flex;
          align-items: center;
          justify-content: space-evenly;
          width: 70%;
          margin: 0 auto;
     }

     &__dealers {
          @extend %sans_bold;
          color: $brand-secondary;
          @include prem(17.97);
     }

     &__filter-text {
          @extend %sans_bold;
          color: $text-primary;
          @include prem(17.97); 
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

     &__label {
          @extend %sans_reg;
          @include prem(11.98);
          margin-left: 0.5rem;
     }
}
</style>

