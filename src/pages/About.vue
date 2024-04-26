<template>
  <q-page class="bg-brown-1 column">
    <h2 class="heading">Pick a color!</h2>
    <div class="q-pa-md row no-wrap items-center justify-around q-gutter-sm">
      <q-icon size="100px" :name="colorpickerSvg" />

      <q-btn
        :dense="$q.screen.xs"
        no-caps
        label="Skin"
        icon-right="colorize"
        color="primary"
      >
        <q-popup-proxy cover transition-show="scale" transition-hide="scale">
          <q-color v-model="colorSkin" />
        </q-popup-proxy>
      </q-btn>

      <q-btn
        :dense="$q.screen.xs"
        no-caps
        label="Jewlery"
        icon-right="colorize"
        color="secondary"
      >
        <q-popup-proxy cover transition-show="scale" transition-hide="scale">
          <q-color v-model="colorJewlery" />
        </q-popup-proxy>
      </q-btn>
    </div>
  </q-page>
</template>

<script>
import { ref, computed } from "vue";

export default {
  setup() {
    const colorSkin = ref("#101510");
    const colorJewlery = ref("#FFC600");

    const colorpickerSvg = computed(() => {
      const skin = colorSkin.value.replace("#", "%23");
      const jewlery = colorJewlery.value.replace("#", "%23");
      return `img:data:image/svg+xml;charset=utf8,<svg width="60" height="26" viewBox="0 0 60 26" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M60.0004 0L42.2539 6.19718L45.0708 14.6479L60.0004 0Z" fill="${skin}"/>
<path d="M-0.000385284 0L17.7461 6.19718L14.9292 14.6479L7.4644 7.32394L6.61933 4.08451L3.73201 3.66197L-0.000385284 0Z" fill="${skin}"/>
<path d="M29.4347 25.2113L16.1953 18.169L21.6883 0H38.308L43.3784 18.169L29.4347 25.2113Z" fill="${skin}"/>
<path d="M53.238 9.57752L51.1253 7.18316L51.8295 6.0564L55.3506 9.85921L50.5619 13.0987L48.4492 11.2677L49.4351 10.2817L50.8436 11.5494L53.238 9.57752Z" fill="${jewlery}"/>
<path d="M37.4648 11.2676L35.4853 12.5275L34.2254 14.5071L32.9656 12.5275L30.986 11.2676L32.9656 10.0078L34.2254 8.0282L35.4853 10.0078L37.4648 11.2676Z" fill="${jewlery}"/>
</svg>`;
    });

    return {
      colorSkin,
      colorJewlery,

      colorpickerSvg,
    };
  },
};
</script>

<style>
.heading {
  display: flex;
  justify-content: center;
}
</style>
