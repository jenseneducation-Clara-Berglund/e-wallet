<template>
  <div class="home">
    <Header title="E-WALLET" />
    <h2>ACTIVE CARD</h2>
    <Card
      color="orange"
      cardnumber="1234 5678 9101 1123"
      cardholder="CARDHOLDER NAME"
      cardname="CHRISTOFFER WALLENBERG"
      validthru="VALID THRU"
      validdate="12/22"
      vendor="bitcoin"
    />

    <CardStack />

    <button class="addANewCardButton">ADD A NEW CARD</button>
  </div>
</template>

<script>
import Header from "../components/Header.vue";
import Card from "../components/Card.vue";
import CardStack from "../components/CardStack.vue";

export default {
  name: "Home",
  components: {
    Header,
    Card,
    CardStack
  }
};
</script>
<style scoped>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
}
h2 {
  font-size: 0.7em;
  color: grey;
}

CardStack {
  height: 40em;
  width: 32em;
}

.addANewCardButton {
  width: 29em;
  height: 6em;
  margin-top: 4em;
  border-radius: 1em;
  border-color: black;
  font-weight: bolder;
}
</style>
