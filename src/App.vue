<template>
  <div class="app"><p>{{ name }} - {{ age }}</p></div>
  <button @click="changeName('Zelda')">change name</button>
  <button @click="changeAge(20)">change age</button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "App",
  components: {},
  data() {
    return {
      name: 'Link',
      age: 25 as number | string
    }
  },
  methods: {
    changeName(name: 'string') {
    this.name = name
    return name
    },
    changeAge(age: number | string) {
      this.age = age
    }
  }
});
</script>

<style></style>
