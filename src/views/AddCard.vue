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
    <cardForm />
    <button class="addCard"></button>
  </div>
</template>
<script>
import Header from "../components/Header.vue";
import Card from "../components/Card.vue";
import CardForm from "../components/CardForm.vue";
export default {
  components: { Header, Card, CardForm }
};
</script>
<style scoped>
h2 {
  font-size: 0.5em;
}
</style>
