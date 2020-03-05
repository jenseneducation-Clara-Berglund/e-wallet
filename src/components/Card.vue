<template>
  <div class="cardWrapper">
    <div class="card" v-bind:style="{ backgroundColor: color }">
      <div class="imgWrapper">
        <blippLogo class="blippLogo" />

        <div v-if="this.vendor === 'bitcoin'">
          <vendorBitcoin class="vendor" />
        </div>
        <div v-if="this.vendor === 'evil'">
          <vendorEvil class="vendor" />
        </div>
        <div v-if="this.vendor === 'blockchain'">
          <vendorBlockchain class="vendor" />
        </div>
        <div v-if="this.vendor === 'ninja'">
          <vendorNinja class="vendor" />
        </div>
      </div>

      <p class="cardnumber">{{ cardnumber }}</p>
      <div class="nameAndDateWrapper">
        <div class="cardHolderAndNameWrapper">
          <p class="cardholder">{{ cardholder }}</p>
          <p class="cardname">{{ cardname }}</p>
        </div>
        <div class="validThruAndDateWrapper">
          <p class="validthru">{{ validthru }}</p>
          <p class="validdate">{{ validdate }}</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import blippLogo from "../assets/chip-dark.svg";
import vendorBitcoin from "../assets/vendor-bitcoin.svg";
import vendorBlockchain from "../assets/vendor-blockchain.svg";
import vendorEvil from "../assets/vendor-evil.svg";
import vendorNinja from "../assets/vendor-ninja.svg";
export default {
  name: "Card",
  props: {
    cardnumber: String,
    cardholder: String,
    cardname: String,
    validthru: String,
    validdate: String,
    color: String,
    vendor: String
  },
  components: {
    blippLogo,
    vendorBitcoin,
    vendorBlockchain,
    vendorEvil,
    vendorNinja
  }
};
</script>
<style scoped>
.cardWrapper {
  display: flex;
  justify-content: center;
}
.card {
  width: 20em;
  height: 14em;
  border-radius: 5%;
  display: flex;
  flex-direction: column;
}

.cardnumber {
  text-align: center;
  font-size: 1.7em;
  color: black;
  margin: 0.1em;
}

.nameAndDateWrapper {
  display: flex;
  justify-content: space-between;
  flex-direction: row;
  margin: 1em;
}
.cardHolderAndNameWrapper {
  display: flex;
  flex-direction: column;
}
.validThruAndDateWrapper {
  display: flex;
  flex-direction: column;
}
.cardholder {
  font-size: 0.7em;
  color: black;
  margin: 0;
  text-align: left;
}
.validthru {
  font-size: 0.7em;
  color: black;
  margin: 0;
  text-align: right;
}
.cardname {
  font-size: 1em;
  color: black;
  margin: 0;
  text-align: left;
}
.validdate {
  color: black;
  font-size: 1em;
  margin: 0;
  text-align: right;
}
.imgWrapper {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.blippLogo {
  margin: 1em;
}

.vendor {
  margin: 1em;
}
</style>
