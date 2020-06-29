<template>
  <div class="search-container">
    <form v-on:submit.prevent>
      <h3>조회 조건</h3>
      <select v-model="selectedCondition">
        <option value="선택 없음">선택 없음</option>
        <option value="name">상점명</option>
        <option value="business">사업자</option>
      </select>
      <input v-model="searchValue" v-on:keyup.enter="searchList" />
      <ul>
        <li v-on:click="searchList">
          <i class="fa fa-search"></i>
          <span>조회</span>
        </li>
      </ul>
    </form>
    <AddInput v-on:handleAddList="handleAddList"></AddInput>
  </div>
</template>

<script>
import AddInput from "./addList";
export default {
  data() {
    return {
      selectedCondition: "선택 없음",
      searchValue: ""
    };
  },
  methods: {
    searchList() {
      if (this.selectedCondition !== "선택 없음" && this.searchValue !== "") {
        this.$emit("searchList", this.selectedCondition, this.searchValue);
        this.clearValue();
      } else {
        alert("분류를 선택하거나 값을 입력해주세요.");
      }
    },
    clearValue() {
      this.selectedCondition = "선택 없음";
      this.searchValue = "";
    },
    handleAddList(value) {
      console.log(value);
      this.$emit("addList", value);
    }
  },
  components: {
    AddInput: AddInput
  }
};
</script>

<style scoped>
.search-container {
  background-color: #ecf0f1;
  padding: 0.5rem 0.7rem;
}
form {
  display: flex;
  align-items: center;
}
ul {
  list-style-type: none;
  display: flex;
  align-items: center;
}
li {
  background-color: #3498db;
  color: white;
  padding: 0.2rem 0.3rem;
  margin-left: 1rem;
}
li:first-child {
  margin-left: 0;
}
select {
  font-size: 17px;
  margin-left: 0.5rem;
  padding: 0.2rem 0.3rem;
}
input {
  padding: 0.2rem 0.3rem;
  font-size: 16px;
  margin-left: 1rem;
  flex: 1;
}
</style>