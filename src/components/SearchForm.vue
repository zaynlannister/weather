<template>
  <div>
    <input @keydown.enter="$emit('search')" v-model="value" @input="changeValue" class="input" type="text" placeholder="Search city">
    <button @click="$emit('search')" class="button">Search</button>
  </div>
</template>

<script>
export default {
  props: {
    modelValue: String,
    isLoading: Boolean
  },

  data() {
    return {
      value: ""
    }
  },

  methods: {
    changeValue() {
      this.$emit("update:modelValue", this.value);
    }
  }
}
</script>

<style scoped>
  .input {
    width: 400px;
    border: 1px solid #fff;
    outline: none;
    padding: 8px 15px;
    border-bottom-left-radius: 5px;
    border-top-left-radius: 5px;
    transition: 100ms all;
  }

  .input:focus {
    border-color: #48484a;
  }

  .button {
    cursor: pointer;
    background-color: #48484a;
    color: #fff;
    border: 1px solid #48484a;
    outline: none;
    padding: 8px 10px;
    border-bottom-right-radius: 5px;
    border-top-right-radius: 5px;
    transition: 100ms all;
  }

  .button:hover {
    background-color: #717070;
  }
</style>