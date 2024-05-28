<script setup>
let selectedItem = defineModel()
function select(event) {
  const siblingElement = event.target.previousSibling
  const linkContent = event.target.innerHTML
  const selectors = document.querySelectorAll('.selector')
  selectors.forEach((element) => {
    element.classList.remove('active')
    element.classList.add('inactive')
  })
  siblingElement.classList.remove('inactive')
  siblingElement.classList.add('active')
  selectedItem.value = linkContent
}
</script>

<template>
  <div id="menu">
    <div class="menu-element">
      <img class="selector active" src="../assets/img/selector.svg" />
      <a href="#" @click="select($event)">Home</a>
    </div>
    <div class="menu-element">
      <img class="selector inactive" src="../assets/img/selector.svg" />
      <a href="#" @click="select($event)">Twitch</a>
    </div>
    <div class="menu-element">
      <img class="selector inactive" src="../assets/img/selector.svg" />
      <a href="#" @click="select($event)">Twitter</a>
    </div>
    <div class="menu-element">
      <img class="selector inactive" src="../assets/img/selector.svg" />
      <a href="#" @click="select($event)">Mastodoon</a>
    </div>
    <div class="menu-element">
      <img class="selector inactive" src="../assets/img/selector.svg" />
      <a href="#" @click="select($event)">Bluesky</a>
    </div>
    <div class="menu-element">
      <img class="selector inactive" src="../assets/img/selector.svg" />
      <a href="#" @click="select($event)">Créditos</a>
    </div>
    <div class="menu-element">
      <img class="selector inactive" src="../assets/img/selector.svg" />
      <a href="#" @click="select($event)">Sobre mi</a>
    </div>
    <div class="menu-element">
      <img class="selector inactive" src="../assets/img/selector.svg" />
      <a href="#" @click="select($event)">??????</a>
    </div>
  </div>
</template>

<style scoped>
#menu {
  width: 297px;
  height: 500px;
  background-image: url('../assets/img/menu.png');
  background-repeat: no-repeat;
  background-size: cover;
  right: 0;
  top: 20px;
  position: absolute;
  padding-top: 40px;
}

a {
  font-family: pkmn;
  font-size: 25px;
  text-decoration: none;
  color: black;
}

.menu-element {
  margin-left: 20px;
  margin-bottom: 30px;
  padding-left: 30px;
}

.menu-element a {
  margin-left: 10px;
}

.selector {
  width: 17px;
}

.active {
  visibility: visible;
}

.inactive {
  visibility: hidden;
}
</style>
