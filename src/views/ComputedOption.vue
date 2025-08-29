<template>
  <div>
    <h3>Computed 속성</h3>
    <p>FirstName: <input type="text" v-model="fname" /></p>
    <p>LastName: <input type="text" v-model="lname" /></p>
    <p>FullName: {{ fullName }}</p>
  </div>
  <div>
    <h3>Watch 속성, 속성의 변경이전, 변경이후 값을 처리</h3>
    <strong>{{ changeName }}</strong>
    <!-- v-on을 @로도 쓸수있다-->
    <button @click="changingName">change</button>
  </div>
  <div>
    <p v-bind:key="i" v-for="(fruit, i) in cartList">
      <strong>{{ fruit.pname }}</strong> - 가격: {{ fruit.price }} - 수량:
      {{ fruit.qty }}
      <input type="number" v-model="fruit.qty" />
    </p>
    <p>
      <strong>총 가격: {{ totalQuantity }}개</strong>
    </p>
    <p>
      <strong>총 수량: {{ totalPrice }}원</strong>
    </p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      msg: "",
      fname: "kildong",
      lname: "Hong",
      cartList: [
        { id: 1, pname: "사과", price: 1000, qty: 2 },
        { id: 2, pname: "포도", price: 2000, qty: 3 },
        { id: 3, pname: "수박", price: 6000, qty: 1 },
      ],
      changeName: "Hong",
    };
  },
  computed: {
    // 계산된 속성
    fullName() {
      return this.fname + "/" + this.lname;
    },
    totalQuantity() {
      return this.cartList.reduce((acc, item) => {
        return acc + item.qty;
      }, 0);
    },
    totalPrice() {
      return this.cartList.reduce((acc, item) => {
        return acc + item.price * item.qty;
      }, 0);
    },
  },
  watch: {
    changeName(next, prev) {
      console.log("변경전: " + prev + ", 변경후: " + next);
    },
  },
  methods: {
    changingName() {
      this.changeName == "Hong"
        ? (this.changeName = "Hwang")
        : (this.changeName = "Hong");
    },
  },
};
</script>
<style scoped>
body {
  margin: auto;
}
</style>
