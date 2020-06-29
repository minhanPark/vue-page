<template>
  <div id="app">
    <Search v-on:searchList="searchList" v-on:addList="addList"></Search>
  </div>
</template>

<script>
import Search from "./components/search";
import AddInput from "./components/addList";

export default {
  data() {
    return {
      stores: [
        { id: 1, name: "옵타움플랫폼", business: "법인", tel: "0517777777" },
        { id: 2, name: "강가네국밥", business: "개인", tel: "0511234567" },
        { id: 3, name: "법인회사예시", business: "법인", tel: "0513456789" }
      ],
      storeList: [],
      nextId: 4, // 추가되었을 때 적용되어야할 id를 나타냄
      inputValue: "",
      selectedStore: {}
    };
  },
  components: {
    Search: Search
  },
  methods: {
    searchList(condition, value) {
      this.storeList = this.stores.filter(store => store[condition] === value);
      console.log(this.storeList);
    },
    addList(value) {
      this.stores.push({ id: this.nextId, ...value });
      this.nextId += 1;
    }
  }
};
</script>

<style>
body {
  background-color: white;
  margin: 0;
}
</style>
