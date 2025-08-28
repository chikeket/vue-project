<template>
  <div>
    <img v-bind:src="imgSrc" v-bind:width="widthVal" />
  </div>
  <div class="container" v-bind:class="{ active: isActive, 'text-red': isRed }">
    Class Binding
  </div>
  <div v-bind:class="clsAry">Class Binding 배열</div>
  <!--:태그 이렇게 적어도 v-bind 적용됨-->
  <div :style="backVal">Style Binding</div>
</template>

<script>
export default {
  data() {
    return {
      imgSrc: require("@/assets/logo.png"),
      widthVal: "100px",
      isActive: false,
      isRed: true,
      activeCls: "active", //따로 써서 v-bind:class=""에 넣어도 된다
      redCls: "text-red",
      clsAry: ["active", "text-red"], //같이 써도 되고
      backVal: { backgroundColor: "red", color: "green" },
    };
  },
};
</script>
<!-- scoped 이 페이지 내에서만 적용 되는 기능임 -->
<style scoped>
.active {
  background-color: green;
  font-weight: bold;
  color: white;
}
.text-red {
  color: red;
}
</style>
