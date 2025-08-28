<template>
  <h3>{{ msg }}</h3>
  <table>
    <thead>
      <tr>
        <th>아이디</th>
        <th>이름</th>
        <th>나이</th>
      </tr>
    </thead>
    <tbody>
      <tr v-bind:key="i" v-for="(prod, i) in data">
        <td>{{ prod.id }}</td>
        <td v-text="prod.name"></td>
        <td>{{ prod.age }}</td>
      </tr>
    </tbody>
  </table>
  <table>
    <thead>
      <tr>
        <th>카테고리</th>
        <th>배송비</th>
        <th>가격</th>
        <th>상품</th>
      </tr>
    </thead>
    <tbody>
      <tr v-bind:key="i" v-for="(prod, i) in prodList">
        <td>{{ prod.category }}</td>
        <td v-text="prod.delivery_price"></td>
        <td>{{ prod.price }}</td>
        <td>{{ prod.product_name }}</td>
      </tr>
    </tbody>
  </table>
</template>
<script>
export default {
  data() {
    return {
      msg: "학생목록",
      data: [
        { id: 1, name: "홍길동", age: 20 },
        { id: 2, name: "김민수", age: 22 },
        { id: 3, name: "최익수", age: 23 },
      ],
      prodList: [],
    };
  },
  mounted() {
    // DataBindingList 컴포넌트가 생성이 되면
    fetch("http://192.168.0.83:3000/products")
      .then((resopnse) => resopnse.json())
      .then((result) => {
        console.log(result);
        this.prodList = result;
      });
  },
};
</script>
<style></style>
