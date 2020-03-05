<template>
  <div class="formContainer">
    <input v-model="cardnumber" class="inputCardNumber" type="text" />
    <input v-model="name" class="inputCardName" style="text" />
    <input v-model="expiresAt" style="text" />
    <input v-model="cvc" style="text" />
    <select v-model="vendor" name="vendors">
      <option value="bitcoin">BitcoinBank</option>
      <option value="evil">EvilBank</option>
      <option value="blockchain">BlockchainCorp</option>
      <option value="ninja">NinjaCorp</option>
    </select>
    <select v-model="color" name="vendors">
      <option value="red">Red</option>
      <option value="orange">Oragne</option>
      <option value="blue">Blue</option>
      <option value="gray">Gray</option>
    </select>
    <!-- $data refererar till hela data-objektet nedan -->
    <button v-on:click="addNewCard($data)" class="addANewCardButton">
      ADD CARD
    </button>
  </div>
</template>
<script>
export default {
  name: "CardForm",
  data: function() {
    return {
      cardnumber: "",
      name: "",
      expiresAt: "",
      cvc: "",
      vendor: "",
      color: ""
    };
  },
  props: {
    addNewCard: Function
  }
};
</script>
<style scoped>
.formContainer {
  display: flex;
  flex-direction: column;
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
