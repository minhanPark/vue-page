<template>
  <div id="app">
    <Search v-on:searchList="searchList" v-on:addList="addList"></Search>
    <StoreList v-bind:store-list="storeList" v-on:selectList="selectList"></StoreList>
    <SelectedList v-bind="selectedStore" v-on:updateSelectedList="updateSelectedList"></SelectedList>
  </div>
</template>

<script>
import Search from "./components/search";
import AddInput from "./components/addList";
import StoreList from "./components/storeList";
import SelectedList from "./components/selectedList";

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
      selectedStore: {}
    };
  },
  components: {
    Search: Search,
    StoreList: StoreList,
    SelectedList: SelectedList
  },
  methods: {
    searchList(condition, value) {
      this.clearSelectedList();
      this.storeList = this.stores.filter(store => store[condition] === value);
      console.log(this.storeList);
    },
    addList(value) {
      this.clearSelectedList();
      this.stores.push({ id: this.nextId, ...value });
      this.nextId += 1;
    },
    selectList(id) {
      console.log("clicked");
      this.selectedStore = this.storeList.filter(store => store.id === id)[0];
      console.log(this.selectedStore);
    },
    clearSelectedList() {
      this.selectedStore = {};
    },
    updateSelectedList(value) {
      const index = this.stores.findIndex(store => store.id == value.id);
      return this.stores.splice(index, 1, value);
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
