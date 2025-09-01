<template>
  <div class="child-container">
    {{ msg }}

    <h3>{{ title }}</h3>
    <div v-if="isShow">
      <p>Likes: {{ likes }}</p>
      <p>isOK ? {{ isOK ? "Yes" : "No" }}</p>
    </div>

    <h3>Member List</h3>
    <ul>
      <li v-for="(family, i) in memberList" :key="i">
        {{ family.name }} - {{ family.age }} year old.
      </li>
    </ul>
    <input v-model="name" />
    <input type="text" v-model="age" />
    <button @click="callParentEvent">call parent event</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      msg: "Child Component",
      name: null,
      age: null,
    };
  },
  props: {
    title: { type: String, default: "Default Title" },
    likes: { type: Number, default: 0 },
    isOK: { type: Boolean, default: false },
    isShow: { type: Boolean, default: true },
    memberList: {
      type: Array,
      default: () => [], //Object, Array => 함수로 초기정의
    },
  },
  methods: {
    callParentEvent() {
      //부모요소를 찾아서 메소드 실행보다는 하위요소에서 부모요소로 이벤트 요청방식이 덜 헷갈림
      this.$emit("child-clicked", { name: this.name, age: this.age }); //부모컴포넌트로 이벤트 송출하겠다는 의미 "이방식을 잘씀"
      // .$emit("메소드이름", 매개변수자리인데 ,로 추가해도 되지만 객체타입으로 전달하는것이 깔끔함)
    },
  },
  mounted() {
    // console.log(this);
    // this.$parent.msg = "부모컴포넌트"; //"이 방식 잘안씀"
  },
};
</script>

<style>
/**/
.child-container {
  border: 2px dotted red;
}
</style>
