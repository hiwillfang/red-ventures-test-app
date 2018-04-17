<template>
  <main class="main" role="main">
       <div class="main__bg"></div>
       <FilterComponent />
       <CardsComponent />
  </main>
</template>

<script>
import FilterComponent from '../components/FilterComponent'
import CardsComponent from '../components/CardsComponent'

export default {
  components: {
       FilterComponent,
       CardsComponent
  }
}
</script>

<style lang="scss" scoped>
@import '~$scss/main';

.main {
     padding: 2rem 0;

     &__bg {
          background-image: url('../assets/water-image.png');
          background-size: cover;
          background-repeat: repeat-x;
          min-height: 140px;
     }

}
</style>
