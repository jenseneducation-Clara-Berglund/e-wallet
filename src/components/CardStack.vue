<template>
  <div class="cardStack">
    <Card
      v-for="(card, index) in cards"
      :style="{ marginTop: index > 0 ? '-11em' : '0em' }"
      :key="JSON.stringify(card)"
      :color="card.color"
      :cardnumber="card.cardnumber"
      :cardname="card.cardname"
      :validthru="card.validthru"
      :validdate="card.validdate"
      :vendor="card.vendor"
      :onClick="() => chooseCard(card)"
    />
  </div>
</template>
<script>
import Card from "./Card.vue";
export default {
  name: "CardStack",
  props: {
    cards: Array,
    chooseCard: Function
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
