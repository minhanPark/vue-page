<template>
  <div>
    <form v-on:submit.prevent>
      <select v-model="selectedCondition">
        <option value="선택 없음">선택 없음</option>
        <option value="name">상점명</option>
        <option value="business">사업자</option>
      </select>
      <input v-model="searchValue" v-on:keyup.enter="searchList" />
      <ul>
        <li>
          <i class="fa fa-search"></i>
          <span>조회</span>
        </li>
        <li>
          <i class="fa fa-plus"></i>
          <span>신규가맹점</span>
        </li>
      </ul>
    </form>
    <span>{{selectedCondition}}</span>
    <span>{{searchValue}}</span>
  </div>
</template>

<script>
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
      }
    },
    clearValue() {
      this.selectedCondition = "선택 없음";
      this.searchValue = "";
    }
  }
};
</script>

<style scoped>
ul {
  list-style-type: none;
}
</style>