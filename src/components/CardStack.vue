<template>
  <div class="cardStack">
    <Card
      v-for="(card, index) in cards"
      :style="{ marginTop: index > 0 ? '-11em' : '0em' }"
      :key="card.cardnumber"
      :color="card.color"
      :cardnumber="card.cardnumber"
      :cardholder="card.cardholder"
      :cardname="card.cardname"
      :validthru="card.validthru"
      :validdate="card.validdate"
      :vendor="card.vendor"
    />
  </div>
</template>
<script>
import Card from "./Card.vue";
export default {
  name: "CardStack",
  props: {
    cards: Array
  },
  components: {
    Card
  }
};
</script>

<style scoped>
.cardStack {
  display: flex;
  flex-direction: column;
}
</style>
