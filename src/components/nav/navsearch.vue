<template>
  <div class="searchcont">
    <input type="text" @keyup.enter="addtodo" v-model="search" />
    <button @click="addtodo">Add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      search: ""
    };
  },
  methods: {
    addtodo() {
      if (this.search !== "") {
        this.$emit("search", this.search);
      }
    }
  }
};
</script>

<style scoped>
input {
  height: 50px;
  width: 300px;
  background-color: #fff;
  color: #0f0e0f;
  font-size: 20px;
}
input:focus {
  outline: none;
}
.searchcont {
  display: flex;
}
button {
  padding: 0px 50px;
  margin-left: 20px;
  background-color: rgb(233, 40, 114);
  border: 0;
  color: #fff;
  font-size: 18px;
  font-weight: 600;
}
button:focus {
  outline: none;
}
button:hover {
  cursor: pointer;
}
@media screen and (max-width: 500px) {
  .searchcont {
    display: block;
  }
  input {
    height: 50px;
    width: 100%;
    font-size: 20px;
  }
  button {
    height: 50px;
    width: 100%;
    margin-left: 0px;
    margin-top: 10px;
    font-size: 17px;
  }
}
</style>
