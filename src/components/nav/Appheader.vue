<template>
  <div>
    <div class="headcont">
      <searchfield @search="search" />
    </div>
  </div>
</template>

<script>
import searchfield from "./navsearch";
export default {
  name: "AppHeader",
  components: {
    searchfield
  },
  data() {
    return {};
  },
  methods: {
    addtodo() {
      console.log("todo added");
    },
    search(e) {
      this.$emit("search", e);
    }
  }
};
</script>

<style scoped>
.headcont {
  padding: 50px 0px;
  background-color: #242641;
  display: flex;
  justify-content: center;
}
@media screen and (max-width: 500px) {
  .headcont {
    display: block;
    padding: 50px 20px;
  }
}
</style>
