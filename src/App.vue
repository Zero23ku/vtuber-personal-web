<script setup>
import MenuLayout from './components/MenuLayout.vue'
import TextWindow from './components/TextWindow.vue'
import { ref, watch } from 'vue'

const defaultText =
  'Bienvenido a mi web personal!' +
  '<br><br>Soy Harpuia. Aca podras encontrar links de mis redes, proyectos, y cosas relacionadas.' +
  '<br><br>Puedes contactarme a través de mis redes.'
let song
let content = defaultText
let isPaused = false
let selectedItem = ref('Home')
let showOptions = false
let isFirstTime = true

function mute(event) {
  let ele = document.getElementById('unown')
  if (isPaused) {
    event.target.innerHTML = 'Pausar'
    ele.play()
  } else {
    event.target.innerHTML = 'Despausar'
    ele.pause()
  }
  isPaused = !isPaused
}

watch(selectedItem, (newValue) => {
  switch (newValue) {
    case 'Home':
      content = defaultText
      break
    case 'Twitch':
      content =
        'Actualmente no tengo días fijos para transmitir, pero al menos hay dos directos a la semana.' +
        '<br><br>Para estar al tanto de cuando hago directo suigueme en mi canal.' +
        '<br><br><a target="_blank" href="https://twitch.tv/harpuia_vt/">CLICKEA AQUI.</a>'
      break
    case 'Twitter':
      content =
        'La forma mas rapida de enterarte cuando habra directo y de las diferentes cosas que estoy haciendo.' +
        '<br><br>Tambien subo fotos de mi gato waton.' +
        '<br><br><a target="_blank" href="https://x.com/harpuiavt">CLICKEA AQUI</href>'
      break
    case 'Mastodoon':
      content = 'Proximamente...'
      break
    case 'Bluesky':
      content = 'Proximamente...'
      break
    case 'Créditos':
      content =
        '- Modelo:<br>-<a target="_blank" href="https://x.com/FuraRoss">Twitter - Furaross</a>' +
        '<br><br>- Logo e imagen del canal:<br>-<a target="_blank" href="https://x.com/psycotastic">Twitter - Psycotastic</a>' +
        '<br><br>- Emotes: <br>-<a target="_blank" href="https://x.com/FuraRoss">Twitter - Furaross</a><br>-<a target="blank_" href="https://x.com/Gishimonn">Twitter - Gishi</a>' +
        '<br><br>- Web: Yo (<a target="_blank" href="https://x.com/harpuiavt">Twitter - HarpuiaVT</a>)'
      break
    case 'Sobre mi':
      content =
        'Soy Harpuia: tu rana ninja favorita.' +
        '<br><br>Alguno de mis intereses son: Pokémon, Megaman, JRPG, juegos Indie, Pokémon TCG, MMORPGs.' +
        '<br><br>En mis directos me podrás encontrar principalmente transmitiendo algo relacionado a lo anterior, desarrollando software.'
      break
    case '??????':
      content = '. . . . . . . .'
      if (isFirstTime) {
        isFirstTime = false
        showOptions = true
        song = document.getElementById('unown')
        song.volume = 0.3
        if (song.paused) {
          song.play()
        }
      }

      break
  }
})
</script>

<template>
  <div id="song-control" v-if="showOptions">
    <a @click="mute" href="#">Pausar</a>
  </div>
  <MenuLayout v-model="selectedItem"></MenuLayout>
  <TextWindow :content="content"></TextWindow>
  <audio id="unown" loop>
    <source src="./assets/audio/Unown.mp3" type="audio/mpeg" />
  </audio>
</template>

<style scoped>
@font-face {
  font-family: pkmn;
  src: url('./assets/font/PKMN RBYGSC.ttf');
}

#song-control {
  background-color: white;
  font-family: pkmn;
  position: absolute;
  left: 10px;
  top: 10px;
  padding: 10px;
}

#song-control a {
}
</style>
