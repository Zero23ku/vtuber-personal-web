<script setup>
const props = defineProps(['content'])
</script>

<template>
  <div id="window">
    <div class="container">
      <p v-html="props.content"></p>
    </div>
  </div>
</template>

<style scoped>
#window {
  background-color: white;
  width: 100%;
  height: auto;
  min-height: 40%;
  position: absolute;
  top: 700px;
  font-family: pkmn;
  font-size: 35px;
  text-decoration: none;
  color: black;
  letter-spacing: 7px;
  line-height: 1.5;
}

.container {
  padding: 10px;
}

p {
  margin-top: 5px;
}
</style>
