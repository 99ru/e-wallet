<template>
  <div>
    <div @click="$emit('sendData', card)" class="card" v-bind:style="cardStyle" >
      
      <span class="logo-style">
        <div class="logos">
          <img :src="wifi" alt="wifi" id="wifiImg" />
          <img :src="chipImg" alt="chip" id="chipImg" />
        </div>
        <img :src="logo" alt="vendor-logo" />
      </span>

      <span class="card-text"> 
        <p id="cardnum">{{ cardNumber }}</p>
        </span>

      <span class="bot">
        <div class="name">
          <p class="cardText">CARDHOLDER NAME</p>
          <p class="cardinfo">{{ userName }}</p>
        </div>
        
        <div class="valid-thru">
          <p class="cardText">VALID THRU</p>
          <p class="cardinfo">{{ `${validMonth}/${validYear}` }}</p>
        </div>

      </span>
    </div>
  </div>
</template>

<script>
export default {
  props: ['card',],

  data() {
    return {
      wifiImg: require('../assets/wifi.svg'),
      chipImg: require('../assets/chip.svg'),
      whiteWifiImg: require('../assets/wifi_white.svg'),
      vendorLogo: require('../assets/bitcoin.svg'),
    };
  },


  methods: {
   /* active(){
     this.card
   } */
  },


  computed: {
    cardStyle() {
      return {
        backgroundColor: this.card.vendor.backgroundColor,
        color: this.card.vendor.fontColor,
      };
    },

    wifi() {
      let inputData = "";
      if (this.card.vendor.name == 'Ninja Bank') {
        inputData = this.whiteWifiImg;
      } else {
        inputData = this.wifiImg;
      }
      return inputData;
    },

    logo() {
      let inputData = "";
      if (this.card.vendor.logo) {
        inputData = this.card.vendor.logo;
      } else {
        inputData = this.vendorLogo;
      }
      return inputData;
    },

    cardNumber() {
      let inputData = "";
      if (this.card.cardNumber) {
        let sub1 = this.card.cardNumber.substring(0, 4);
        let sub2 = this.card.cardNumber.substring(4, 8);
        let sub3 = this.card.cardNumber.substring(8, 12);
        let sub4 = this.card.cardNumber.substring(12, 16);
        inputData = `${sub1} ${sub2} ${sub3} ${sub4}`;
      } else {
        inputData = "";
      }
      return inputData;
    },

    userName() {
      let inputData = "";
      if (this.card.name) {
        inputData = this.card.name;
      } else {
        inputData = `Firstname Lastname`;
      }
      return inputData;
    },

    validMonth() {
      let inputData = "";
      if (this.card.month) {
        inputData = this.card.month;
      } else {
        inputData = "MM";
      }
      return inputData;
    },
    
    validYear() {
      let inputData = "";
      if (this.card.year) {
        inputData = this.card.year.substring(2, 4);
      } else {
        inputData = "YY";
      }
      return inputData;
    },
  },
};
</script>

<style scoped>
.name {
  margin-left: 10px;
}
.valid-thru {
  margin-right: 5px;
}
.card-text {
  font-size: 5px;
  font-family: 'PT Mono', monospace;
  text-align: left;
}
.cardinfo {
  font-size: 15px;
  font-family: 'PT Mono', monospace;
  margin-top: 5px;
  letter-spacing: 0.1rem;
}
#cardnum {
  text-align: left;
  font-size: 23px;
  letter-spacing: 6px;
  margin-top: 10px;
  font-family: 'PT Mono', monospace;
}
.logos {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
  margin-left: 20px;
}
.logo-style {
  display: flex;
  justify-content: space-between;
}
.bot {
  display: flex;
  justify-content: space-between;
}
.card {
  background-color: #D0D0D0;
  box-shadow: 0px 0px 5px 5px rgba(0, 0, 0, 0.32);
}

/* div.card{
  transform: translateY(10%);
}
 */

</style>
