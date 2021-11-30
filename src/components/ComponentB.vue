<template>
  <div>
    <div contenteditable @input="setThought($event.target.innerText)">
      {{ thought }}
    </div>
    <div class="">
      <button @click="readMind">What is A thinking?</button> {{ otherThought }}
    </div>
  </div>
</template>

<script>
export default {
  name: "ComponentB",
  data() {
    return {
      thought: 'I like school a tiny bit',
      otherThought: '',
    };
  },
  methods: {
    setThought(value) {
      this.thought = value
    },
    readMind() {
      this.otherThought = this.$parent.$refs.componentA.thought
    }
  },
};
</script>

<style scoped>
div {
  border: 1px solid green;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}
</style>
