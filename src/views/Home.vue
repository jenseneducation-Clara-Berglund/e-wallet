<template>
  <div class="home">
    <Header title="E-WALLET" />
    <h2>ACTIVE CARD</h2>
    <Card
      v-if="chosenCard !== null"
      :color="chosenCard.color"
      :cardnumber="chosenCard.cardnumber"
      :cardname="chosenCard.cardname"
      :validdate="chosenCard.validdate"
      :vendor="chosenCard.vendor"
      :onClick="() => {}"
    />

    <CardStack
      style="margin-top:2em;"
      v-bind:cards="cards.filter(c => c.cardnumber !== chosenCard.cardnumber)"
      v-bind:chooseCard="chooseCard"
    />

    <button v-on:click="addNewCard" class="addANewCardButton">
      ADD A NEW CARD
    </button>
  </div>
</template>

<script>
import Header from "../components/Header.vue";
import Card from "../components/Card.vue";
import CardStack from "../components/CardStack.vue";

export default {
  name: "Home",
  methods: {
    addNewCard: function() {
      window.location = "/AddCard";
    },
    chooseCard: function(card) {
      this.chosenCard = card;
      localStorage.setItem("chosenCard", JSON.stringify(card));
    }
  },
  data: function() {
    return {
      cards: JSON.parse(localStorage.getItem("cards")) || [],
      chosenCard: JSON.parse(localStorage.getItem("chosenCard")) || null
    };
  },
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
