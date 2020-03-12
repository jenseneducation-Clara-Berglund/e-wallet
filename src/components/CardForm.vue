<template>
  <div class="formContainer">
    <p>CARD NUMBER</p>
    <input
      v-model="cardnumber"
      maxlength="16"
      class="inputCardNumber"
      type="text"
    />
    <p>CARDHOLDER NAME</p>
    <input v-model="name" class="inputCardName" type="text" />

    <div
      style="display: flex; flex-direction:row; justify-content:space-between"
    >
      ¨
      <p>MONTH</p>
      <p>YEAR</p>
    </div>
    <div
      style="display: flex;flex-direction:row; justify-content:space-between"
    >
      <div>
        <select style="width: 14em; " v-model="expiresAtMonth" name="expiresAt">
          <option v-for="n in 12" :key="n">{{ n >= 10 ? n : "0" + n }}</option>
        </select>
        <select
          style="width: 14em;margin-left: 1em;"
          v-model="expiresAtYear"
          name="expiresAt"
        >
          <option v-for="n in 4" :key="n">{{ 2020 + n }}</option>
        </select>
      </div>
    </div>
    <p>VENDOR</p>
    <select v-model="vendor" name="vendors">
      <option value="bitcoin">BitcoinBank</option>
      <option value="evil">EvilBank</option>
      <option value="blockchain">BlockchainCorp</option>
      <option value="ninja">NinjaCorp</option>
    </select>
    <!-- $data refererar till hela data-objektet nedan -->
    <button
      @mouseover="buttonMouseOver = true"
      @mouseleave="buttonMouseOver = false"
      v-on:click="addNewCard($data)"
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
export default {
  name: "CardForm",
  data: function() {
    return {
      cardnumber: "",
      name: "",
      expiresAtYear: "",
      expiresAtMonth: "",
      vendor: "",
      buttonMouseOver: false
    };
  },
  props: {
    addNewCard: Function,
    onCardFormUpdate: Function
  },
  watch: {
    cardnumber: function() {
      this.onCardFormUpdate(this.$data);
    },
    name: function() {
      this.onCardFormUpdate(this.$data);
    },
    vendor: function() {
      this.onCardFormUpdate(this.$data);
    },
    expiresAtYear: function() {
      this.onCardFormUpdate(this.$data);
    },
    expiresAtMonth: function() {
      this.onCardFormUpdate(this.$data);
    }
  }
};
</script>
<style scoped>
.formContainer {
  display: flex;
  flex-direction: column;
  padding-top: 1em;
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

.inputCardNumber {
  height: 3em;
  border: 1px solid #000;
  border-radius: 0.25rem;
  padding: 0.5em;
  margin-top: 0.2em;
}

.inputCardName {
  height: 3em;
  border: 1px solid #000;
  border-radius: 0.25em;
  padding: 0.5em;
  margin-top: 0.2em;
}

select {
  width: 29em;
  height: 3.5em;
  border-radius: 0.25em;
  border: 1px solid #000;
}

p {
  font-size: 0.7em;
  width: 45%;
}
</style>
