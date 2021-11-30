<template>
  <div>
    <div contenteditable @input="setThought($event.target.innerText)">
      {{ thought }}
    </div>
    <div>
      <button @click="readMind">What is B thinking?</button> {{ otherThought }}
    </div>
  </div>
</template>

<script>
export default {
  name: "ComponentA",
  data() {
    return {
      thought: 'I should steal a cookie',
      otherThought: '',
    };
  },
  methods: {
    setThought(value) {
      this.thought = value;
      this.$parent.$refs.componentB.setThought(value);
    },
    readMind() {
      this.otherThought = this.$parent.$refs.componentB.thought
    }
  },
};
</script>

<style scoped>
div {
  border: 1px solid red;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}
</style>
