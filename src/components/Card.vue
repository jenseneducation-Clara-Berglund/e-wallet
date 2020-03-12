<template>
  <div class="cardWrapper" v-on:click="onClick()">
    <div
      class="card"
      v-bind:style="{ backgroundColor: getBackgroundColorForVendor(vendor) }"
    >
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

      <p
        class="cardnumber"
        v-bind:style="{ color: getTextColorForVendor(vendor) }"
      >
        {{ formatCardNumber(cardnumber) }}
      </p>
      <div class="nameAndDateWrapper">
        <div class="cardHolderAndNameWrapper">
          <p
            class="cardholder"
            v-bind:style="{ color: getTextColorForVendor(vendor) }"
          >
            CARDHOLDER NAME
          </p>
          <p
            class="cardname"
            v-bind:style="{ color: getTextColorForVendor(vendor) }"
          >
            {{ !!cardname ? cardname.toUpperCase() : "" }}
          </p>
        </div>
        <div class="validThruAndDateWrapper">
          <p
            class="validthru"
            v-bind:style="{ color: getTextColorForVendor(vendor) }"
          >
            VALID THRU
          </p>
          <p
            class="validdate"
            v-bind:style="{ color: getTextColorForVendor(vendor) }"
          >
            {{ !!validdate ? validdate.toUpperCase() : "" }}
          </p>
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
    cardname: String,
    validdate: String,
    vendor: String,
    onClick: Function
  },
  methods: {
    getBackgroundColorForVendor: function(vendor) {
      switch (vendor) {
        case "ninja":
          return "#222";
        case "evil":
          return "#f33355";
        case "blockchain":
          return "#8b58f9";
        case "bitcoin":
          return "#ffae34";
        default:
          return "#d0d0d0";
      }
    },
    getTextColorForVendor: function(vendor) {
      switch (vendor) {
        case "ninja":
          return "#fff";
        case "evil":
          return "#fff";
        case "blockchain":
          return "#fff";
        case "bitcoin":
          return "#000";
        default:
          return "#000";
      }
    },
    formatCardNumber: function(numberString) {
      if (numberString.length === 0) {
        return "";
      }
      var chunks = numberString.match(/.{1,4}/g);
      return chunks.join(" ");
    }
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
  border-radius: 1em;
  box-shadow: 2px 2px 0px 0px rgba(0.5, 0.5, 0.5, 0.2);
}
.card {
  width: 20em;
  height: 14em;
  border-radius: 1em;
  display: flex;
  flex-direction: column;
}

.cardnumber {
  text-align: center;
  font-size: 1.6em;
  height: 3em;
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
  height: 1.2em;
}
.validdate {
  color: black;
  font-size: 1em;
  margin: 0;
  text-align: right;
  height: 1.2em;
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
