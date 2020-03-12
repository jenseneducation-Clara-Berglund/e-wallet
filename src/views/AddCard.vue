<template>
  <div class="addCard">
    <Header title="ADD NEW CARD" />
    <p
      style="margin-bottom: 0; font-weight: bold; font-size: 0.8em; color: grey"
    >
      NEW CARD
    </p>
    <Card
      imageURL="../assets/lo"
      :cardnumber="cardnumber"
      :cardname="cardname"
      :validdate="validdate"
      :vendor="vendor"
    />
    <!-- addNewCard är en funktion som blir tillgänglig för komponenten CardForm via dess `props` -->
    <CardForm
      v-bind:addNewCard="addNewCard"
      v-bind:onCardFormUpdate="onCardFormUpdate"
    />
  </div>
</template>
<script>
import Header from "../components/Header.vue";
import Card from "../components/Card.vue";
import CardForm from "../components/CardForm.vue";
export default {
  components: { Header, Card, CardForm },

  data: function() {
    return {
      cardnumber: "",
      cardname: "",
      validdate: "MM/YY",
      vendor: null
    };
  },

  methods: {
    onCardFormUpdate: function(cardObject) {
      this.cardnumber = cardObject.cardnumber;
      this.cardname = cardObject.name;
      if (cardObject.expiresAtMonth !== "" && cardObject.expiresAtYear !== "") {
        this.validdate =
          cardObject.expiresAtMonth +
          "/" +
          cardObject.expiresAtYear.substring(2);
      } else {
        this.validdate = "MM/YY";
      }
      this.vendor = cardObject.vendor;
    },
    addNewCard: function(cardObject) {
      if (cardObject.cardnumber.length !== 16) {
        alert("Kortet måste innehålla 16 siffror");
        return;
      }
      if (cardObject.name === "") {
        alert("Kortet måste innehålla ett namn");
        return;
      }
      if (cardObject.expiresAtMonth === "" || cardObject.expiresAtYear === "") {
        alert("Kortet måste innehålla ett utgångsdatum");
        return;
      }
      if (cardObject.vendor === null) {
        alert("Kortet måste innehålla en utgivare");
        return;
      }

      let cards = JSON.parse(localStorage.getItem("cards")) || [];
      let card = {
        cardnumber: cardObject.cardnumber,
        cardname: cardObject.name,
        validdate:
          cardObject.expiresAtMonth +
          "/" +
          cardObject.expiresAtYear.substring(2),
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
