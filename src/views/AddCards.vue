<template>
  <div class="add-cards">

    <header >
      <h1>ADD A NEW BANK CARD</h1>
      <p>NEW CARD</p>
    </header>

    <div id="form">
      <Card :card="card" :vendors="vendors" />

      <form class="form" @submit.prevent="submit">
        <label for="card-number">CARD NUMBER</label>
        <input
          type="text"
          name="card-number"
          class="card-number"
          v-model="card.cardNumber"
          maxlength="16"
        />

        <label for="cardholder-name">CARDHOLDER NAME</label>
        <input
          type="text"
          name="cardholder-name"
          placeholder="FIRSTNAME LASTNAME"
          class="cardholder-name"
          v-model="card.name"
          maxlength="26"
        />

        <div class="date">
          <div class="valid">
            <label for="month">MONTH</label>
            <select name="month" v-model="card.month">
              <option
                v-for="month in months"
                :key="month"
                value:value="month"
                name="month"
              >
                {{ month }}
              </option>
            </select>
          </div>

          <div class="valid">
            <label for="year">YEAR</label>
            <select name="year" v-model="card.year">
              <option
                v-for="year in years"
                :key="year"
                value:value="year"
                name="year"
              >
                {{ year }}
              </option>
            </select>
          </div>
        </div>

        <label for="vendor">VENDOR</label>
        <select class="vendor" name="vendor" v-model="card.vendor">
          <option
            v-for="vendor in vendors"
            :key="vendor.name"
            :value="vendor"
            name="vendor"
          >
            {{ vendor.name }}
          </option>
        </select>
        <br>
        <button class="add-card-button" @submit="submit">ADD CARD</button>
      </form>
    </div>
  </div>
</template>

<script>
import Card from "../components/Card.vue";

export default {
  components: { Card },

  data() {
    return {
      card: {
        cardNumber: "",
        name: "",
        year: "",
        month: "",
        vendor: {},
      },
      months: ["1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11", "12"],
      years: ["2022", "2023", "2024", "2025", "2026"],

      vendors: [
        {
          name: "Bitcoin Inc",
          backgroundColor: "#FFAE34",
          fontColor: "black",
          logo: require("../assets/bitcoin.svg"),
        },
        {
          name: "Ninja Bank",
          backgroundColor: "#222222",
          fontColor: "white",
          logo: require("../assets/ninja.svg"),
        },
        {
          name: "Block Chain Inc",
          backgroundColor: "#8B58F9",
          fontColor: "white",
          logo: require("../assets/blockchain.svg"),
        },
        {
          name: "Evil Corp",
          backgroundColor: "#F33355",
          fontColor: "white",
          logo: require("../assets/evil.svg"),
        },
      ],
    };
  },

  methods: {
    submit() {
      console.log(this.card);
      this.$emit("toggleView");
      this.$emit("emit-card", this.card);
    },
  },
};
</script>



<style scoped>
header {
  text-align: center;
}

form{
  margin-top: 40px;
}

.add-cards {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form {
  display: flex;
  flex-direction: column;
}

input,
select {
  font-size: 14px;
  border-radius: 8px;
  min-height: 56px;
}

label {
  margin: 5px;
  margin-top: 10px;
}

.card-number {
  height: 56px;
  width: 382px;
}

.date {
  display: flex;
  justify-content: space-between;
  margin-bottom: 35px;
}

.valid {
  height: 56px;
  width: 170px;
  display: flex;
  flex-direction: column;
}

.vendor {
  height: 56px;
  width: 382px;
}

.add-new-card-button {
  border: none;
  background-color: black;
  color: white;
}

.add-card-button:hover {
  background-color: rgb(20, 20, 20);
  color: white;
}
</style>
