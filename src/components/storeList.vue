<template>
  <div class="list-container">
    <h3>가맹점 정보</h3>
    <table>
      <tr>
        <th>가맹점 ID</th>
        <th>가맹점명</th>
        <th>가맹점 구분</th>
        <th>전화번호</th>
      </tr>
      <tr>
        <td colspan="4" v-if="storeList.length === 0">No data to display</td>
      </tr>
      <tr v-for="list in storeList" v-bind:key="list.id">
        <td>{{list.id}}</td>
        <td>{{list.name}}</td>
        <td>{{list.business}}</td>
        <td>{{list.tel}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import Vue from "vue";

export default {
  props: ["storeList"]
};
</script>

<style scoped>
.list-container {
  width: 100%;
  margin: 0 auto;
  padding: 0.3rem 0.5rem;
  box-sizing: border-box;
}
h3 {
  background-color: #bdc3c7;
  padding: 0.3rem 0.4rem;
  font-size: 14px;
  margin-bottom: 0;
}

table {
  width: 100%;
  border: none;
  border: 1px solid #bdc3c7;
  border-collapse: collapse;
}
tr:first-child {
  background-color: #ecf0f1;
  border-top: 0;
}
tr,
td {
  border: 1px solid #bdc3c7;
}
tr:hover {
  background-color: #ecf0f1;
}
td {
  text-align: center;
}
</style>