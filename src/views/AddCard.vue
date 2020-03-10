<template>
  <div class="addCard">
    <Header title="ADD A NEW BANK CARD" />
    <h2>NEW CARD</h2>
    <Card
      color="lightgrey"
      imageURL="../assets/lo"
      cardnumber="XXXX XXXX XXXX XXXX"
      cardname="FIRSTNAME LASTNAME"
      cardholder="CARDHOLDER NAME"
      validthru="VALID THRU"
      validdate="MM/YY"
    />
    <!-- addNewCard är en funktion som blir tillgänglig för komponenten CardForm via dess `props` -->
    <CardForm v-bind:addNewCard="addNewCard" />
  </div>
</template>
<script>
import Header from "../components/Header.vue";
import Card from "../components/Card.vue";
import CardForm from "../components/CardForm.vue";
export default {
  components: { Header, Card, CardForm },

  methods: {
    addNewCard: function(cardObject) {
      let cards = JSON.parse(localStorage.getItem("cards")) || [];
      let card = {
        cardnumber: cardObject.cardnumber,
        cardname: cardObject.name,
        validdate: cardObject.expiresAt,
        color: cardObject.color,
        vendor: cardObject.vendor
      };
      cards.push(card);
      localStorage.setItem("cards", JSON.stringify(cards));
      localStorage.setItem("chosenCard", JSON.stringify(card));
      window.location = "/";
    }
  }
};
</script>
<style scoped>
.addCard {
  display: flex;
  flex-direction: column;
  align-items: center;
}

h2 {
  display: flex;
  flex-direction: center;
  font-size: 0.5em;
}
</style>
