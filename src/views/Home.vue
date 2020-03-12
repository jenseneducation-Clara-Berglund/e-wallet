<template>
  <div class="home">
    <Header title="E-WALLET" />
    <h2>ACTIVE CARD</h2>
    <Card
      v-if="chosenCard !== null"
      :cardnumber="chosenCard.cardnumber"
      :cardname="chosenCard.cardname"
      :validdate="chosenCard.validdate"
      :vendor="chosenCard.vendor"
      :onClick="() => {}"
    />

    <CardStack
      style="margin-top:2em;"
      v-bind:cards="cards"
      v-bind:chooseCard="chooseCard"
    />

    <button
      @mouseover="buttonMouseOver = true"
      @mouseleave="buttonMouseOver = false"
      v-on:click="addNewCard"
      v-bind:style="{
        color: buttonMouseOver ? 'white' : 'black',
        background: buttonMouseOver ? 'black' : 'white'
      }"
      class="addANewCardButton"
    >
      ADD CARD
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
      chosenCard: JSON.parse(localStorage.getItem("chosenCard")) || null,
      buttonMouseOver: false
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
  font-family: PT Mono, monospace;
  height: 4em;
  padding: 0em 6em;
  margin-top: 2em;
  border-radius: 0.6em;
  border-color: black;
  font-weight: bolder;
  font-size: 18px;
}
</style>
