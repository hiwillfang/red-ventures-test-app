<template>
   <div class="cards">
     <div class="cards___card-wrap" v-for="dealer in dealers" :key="dealer.data.id">
        <h2 class="cards__heading">{{ dealer.data.name }}</h2>
     </div>
   </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'CardsComponent',
  data() {
       return {
            dealers: []
       }
  },
  mounted() {
       axios.get('../../static/json/dealers.json')
       .then(response => {
        this.dealers = response.data.dealers
        console.log(response.data);
      })
      .catch(err => {
        console.log(err);
      })
  },
}

</script>

<style lang="scss" scoped>
@import '~$scss/main';

.cards {
  display: flex;
  justify-content: space-evenly;

  &__card-wrap {

  }

  &__heading {
    @extend %sans_light;
    @include prem(26);
    text-align: center;
    border-bottom: 1px solid $gray;
  }

}

</style>


