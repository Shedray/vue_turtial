<template>
  <div>
    {{ todo.text }}
    <button @click="$emit('remove', todo.id)">完成</button>
  </div>
</template>
<script>
export default {
  name: "toDoListItem",
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      text: "测试",
    };
  },
};
</script>