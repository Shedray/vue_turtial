<template>
  <div>
    <input type="text" :value="value" v-on="listeners" />
  </div>
</template>
<script>
export default {
  name: "toDoInput",
  props: {
    value: {
      type: String,
    },
  },
  computed: {
    listeners() {
      return {
        // Pass all component listeners directly to input
        ...this.$listeners,
        // Override input listener to work with v-model
        input: (event) => this.$emit("input", event.target.value),
      };
    },
  },
};
</script>