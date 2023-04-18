<template>
  <div class="row">
    <div class="col-8">
      <h3>Nested draggable</h3>
      <nested-draggable :tasks="list" />
    </div>

<!--    <rawDisplayer class="col-3" :value="list" title="List" />-->
  </div>
</template>

<script>
import nestedDraggable from "./nested";
export default {
  name: "nested-example",
  display: "Nested",
  order: 2,
  components: {
    nestedDraggable
  },
  data() {
    return {
      list: [
        {
          name: "task 1",
          depth: 1,
          tasks: [
            {
              depth: 2,
              name: "task 2",
              tasks: []
            },
            {
              depth: 2,
              name: "task 2-1",
              tasks: []
            },
            {
              depth: 2,
              name: "task 2-2",
              tasks: []
            }
          ]
        },
        {
          depth: 1,
          name: "task 3",
          tasks: [
            {
              depth: 2,
              name: "task 4",
              tasks: []
            }
          ]
        },
        {
          depth: 1,
          name: "task 5",
          tasks: []
        }
      ]
    };
  }
};
</script>
<style scoped></style>
