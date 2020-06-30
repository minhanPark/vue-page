<template>
  <div>
    <input readonly v-model="id" />
    <input v-model="name" />
    <input v-model="business" />
    <input v-model="tel" />
    <button v-on:clicl="handleClick">수정</button>
  </div>
</template>

<script>
export default {
  props: ["id", "name", "business", "tel"],
  data() {
    return {
      id: this.id,
      name: this.name,
      business: this.business,
      tel: this.tel
    };
  },
  //   created() {
  //     this.data.id = this.id;
  //     this.data.name = this.name;
  //     this.data.business = this.business;
  //     this.data.tel = this.tel;
  //   },
  methods: {
    handleClick() {
      const updateArr = {
        id: this.id,
        name: this.name,
        business: this.business,
        tel: this.tel
      };
      this.$emit("updateSelectedList", updateArr);
    }
  }
};
</script>

<style>
</style>