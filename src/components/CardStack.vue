<template>
  <div>
    <card
      color="#F7433D"
      cardnumber="6666 6666 6666 6666"
      cardholder="CARDHOLDER NAME"
      cardname="CHRISTOFFER WALLENBERG"
      validthru="VALID THRU"
      validdate="10/23"
      vendor="evil"
    />
    <card
      color="#974FD6"
      cardnumber="1234 5678 9101 1213"
      cardholder="CARDHOLDER NAME"
      cardname="CHRISTOFFER WALLENBERG"
      validthru="VALID THRU"
      validdate="10/23"
      vendor="blockchain"
    />
    <card
      color="#444343"
      cardnumber="1415 1617 1819 2021"
      cardholder="CARDHOLDER NAME"
      cardname="CHRISTOFFER WALLENBERG"
      validthru="VALID THRU"
      validdate="10/23"
      vendor="ninja"
    />
  </div>
</template>
<script>
import Card from "./Card.vue";
export default {
  name: "CardStack",
  compontents: {
    Card
  }
};
</script>

<style scoped>
card {
  height: 30 em;
  width: 30em;
}
div {
  height: 60em;
  width: 30em;
}
</style>
