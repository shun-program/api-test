<template>
  <div class="home">
    <input maxlength='7' type="text" v-model="zipcode" />
    <button @click="getAddress">住所自動入力</button>
    <p>Address：{{ address }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      zipcode: "",
      address: ""
    };
  },
  methods: {
    getAddress() {
      axios.get(`https://apis.postcode-jp.com/api/v3/postcodes/${this.zipcode}?apikey=vMbIrYHIZAB02EbOoLL3Q5o3BhFotWZA3t9Ci7d`).then((result) => {
        this.address = result.data.allAddress;
      });
    },
  },
};

</script>
