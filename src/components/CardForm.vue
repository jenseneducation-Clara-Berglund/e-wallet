<template>
  <div class="formContainer">
    <p>CARD NUMBER</p>
    <input v-model="cardnumber" class="inputCardNumber" type="text" />
    <p>CARDHOLDER NAME</p>
    <input v-model="name" class="inputCardName" style="text" />
    <p>VALID THRU</p>
    <div class="validThruAndCvcContainer">
      <input v-model="expiresAt" style="text" />
      <p>CVC</p>

      <input v-model="cvc" style="text" />
    </div>
    <p>VENDOR</p>
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

.validThruAndCvcContainer {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  border-radius: 1em;
}

.addANewCardButton {
  width: 29em;
  height: 6em;
  margin-top: 4em;
  border-radius: 1em;
  border-color: black;
  font-weight: bolder;
}

.inputCardNumber {
  width: 29em;
  height: 3em;
  border-radius: 1em;
}

.inputCardName {
  width: 29em;
  height: 3em;
  border-radius: 1em;
}

input {
  width: 10em;
  height: 3em;
  border-radius: 1em;
}
select {
  width: 29em;
  height: 3em;
  border-radius: 1em;
}

p {
  font-size: 0.7em;
}
</style>
