<template>
  <draggable class="dragArea" tag="ul" :list="tasks" :group="{ name: 'g1' }" :move="onMoveCallback">
    <li v-for="(el, i) in tasks" :key="`${el.name}_${i}_${el.depth}`">
      <p>{{ el.name }}</p>
      <button v-if="el.depth === 1" @click="onAdd(el)">+</button>
      <button v-if="el.depth === 1" @click="onoff(i)">펼쳤다 접기</button>
      <nested-draggable :tasks="el.tasks" v-if="openIndex.includes(i)"/>
    </li>
  </draggable>
</template>
<script>
import draggable from "vuedraggable";
export default {
  props: {
    tasks: {
      required: true,
      type: Array
    }
  },
  components: {
    draggable
  },
  name: "nested-draggable",
  data() {
    return {
      openIndex: []
    }
  },
  methods: {
    onMoveCallback(evt) {

      return evt.from === evt.to
    },
    onAdd(a) {
      console.log(a)
      console.log('onAdd')
      a.tasks.push({
        name: "task 2",
        depth: 2,
        tasks: []
      })
    },
    onoff(i) {
      if (this.openIndex.includes(i)) {
        this.openIndex.splice(this.openIndex.indexOf(i), 1)
      } else {
        this.openIndex.push(i)
      }
    }
  }
};
</script>
<style scoped>
.dragArea {
  min-height: 50px;
}
</style>
