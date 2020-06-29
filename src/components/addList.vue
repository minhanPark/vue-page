<template>
  <div class="container">
    <div class="input-container">
      <div class="input-wrapper">
        <div class="label-wrapper">
          <label for="name">가맹점명</label>
        </div>
        <input name="name" v-model="nameInput" placeholder="옵타움플랫폼" />
      </div>
      <div class="input-wrapper">
        <div class="label-wrapper">
          <label for="business">사업자구분</label>
        </div>
        <input name="business" v-model="businessInput" placeholder="법인 또는 개인" />
      </div>
      <div class="input-wrapper">
        <div class="label-wrapper">
          <label for="tel">전화번호</label>
        </div>
        <input name="tel" v-model="telInput" placeholder="0517896754" />
      </div>
    </div>
    <ul>
      <li v-on:click="handleAddList">
        <i class="fa fa-plus"></i>
        <span>신규가맹점</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nameInput: "",
      businessInput: "",
      telInput: ""
    };
  },
  methods: {
    handleAddList() {
      const newList = {
        name: this.nameInput,
        business: this.businessInput,
        tel: this.telInput
      };
      this.$emit("handleAddList", newList);
      this.clearValue();
    },
    clearValue() {
      this.nameInput = "";
      this.businessInput = "";
      this.telInput = "";
    }
  }
};
</script>

<style scoped>
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
.container {
  display: flex;
}
.input-container {
  display: flex;
  flex: 1;
}
.input-wrapper {
  background-color: #bdc3c7;
  padding: 0.4rem 0.5rem;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.label-wrapper {
  text-align: center;
  margin-bottom: 0.4rem;
}
.label-wrapper label {
  font-size: 14px;
}
.input-wrapper input {
  padding: 0.2rem 0.3rem;
  width: 90%;
}
</style>