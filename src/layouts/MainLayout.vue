<template>
  <q-layout view="lHh lpR lff">
    <q-header class="bg-primary text-white">
      <q-toolbar>
        <q-toolbar-title class="q-pt-md q-ml-xl"> Bar toolbar </q-toolbar-title>
      </q-toolbar>
      <div class="q-pt-xl q-mb-xl q-ml-xl">
        <q-chip :ripple="false">{{ todaysDate }}</q-chip>
      </div>
      <q-img
        class="header-image absolute-top"
        src="../assets/abstract-bg.svg"
      ></q-img>
    </q-header>

    <q-drawer v-model="drawer" show-if-above :width="280" :breakpoint="800">
      <q-scroll-area
        style="
          height: calc(100% - 182px);
          margin-top: 182px;
          border-right: 1px solid #ddd;
        "
      >
        <q-list padding>
          <q-item to="/todo" exact clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>

            <q-item-section> Todo </q-item-section>
          </q-item>

          <q-item to="/help" exact clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>

            <q-item-section> Help </q-item-section>
          </q-item>

          <q-item to="/" exact clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="font_download" />
            </q-item-section>

            <q-item-section> About me </q-item-section>
          </q-item>

          <q-item to="/contacts" exact clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="contacts" />
            </q-item-section>

            <q-item-section> Contacts </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

      <q-img class="absolute-top background" style="height: 182px">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="../assets/avatar.png" />
          </q-avatar>
          <div class="text-weight-bold">Mary Andreychenko</div>
          <div>rookie.mary@gmail.com</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <router-view v-slot="{ Component }">
        <keep-alive>
          <component :is="Component" />
        </keep-alive>
      </router-view>
    </q-page-container>

    <q-footer class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title class="q-ml-xl">
          <div>Footer</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from "vue";
import { date } from "quasar";

export default {
  setup() {
    return {
      drawer: ref(false),
    };
  },
  computed: {
    todaysDate() {
      const timeStamp = Date.now();
      return date.formatDate(timeStamp, "D MMMM YYYY");
    },
  },
};
</script>

<style lang="scss">
.header-image {
  height: 100%;
  z-index: -1;
}

.background {
  background-color: $primary;
}
</style>
