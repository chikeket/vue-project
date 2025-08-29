<template>
  <div>{{ msg }}</div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      msg: "Axios 연습",
      prodList: [],
    };
  },
  methods: {
    async getProdList() {
      let response = await axios.post(
        "http://localhost:3000/api/productList",
        []
      );
      return response.data;
    },
  },
  mounted() {
    this.prodList = this.getProdList();
    console.log(this.prodList);
  },
};
</script>
<style></style>
