<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title> Recherche RTC </q-toolbar-title>

        <div>Version Alpha 2407</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list> </q-list>
    </q-drawer>

    <q-page-container>
      <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
        <div class="row" filled>
          <q-icon name="format_size" style="color: #ccc; font-size: 2em" />
          <q-input
            v-model="text"
            label="Tapez votre code nomenclature"
            name="codeNom"
            style="width: 30%"
          />

          <q-input
            v-model="text"
            label="Decrivez votre RTC"
            name="rtc"
            class="col offset-1"
          />
        </div>
      </q-form>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

const linksList = [
  {
    title: "Docs",
    caption: "quasar.dev",
    icon: "school",
    link: "https://quasar.dev",
  },
  {
    title: "Github",
    caption: "github.com/quasarframework",
    icon: "code",
    link: "https://github.com/quasarframework",
  },
  {
    title: "Discord Chat Channel",
    caption: "chat.quasar.dev",
    icon: "chat",
    link: "https://chat.quasar.dev",
  },
  {
    title: "Forum",
    caption: "forum.quasar.dev",
    icon: "record_voice_over",
    link: "https://forum.quasar.dev",
  },
  {
    title: "Twitter",
    caption: "@quasarframework",
    icon: "rss_feed",
    link: "https://twitter.quasar.dev",
  },
  {
    title: "Facebook",
    caption: "@QuasarFramework",
    icon: "public",
    link: "https://facebook.quasar.dev",
  },
  {
    title: "Quasar Awesome",
    caption: "Community Quasar projects",
    icon: "favorite",
    link: "https://awesome.quasar.dev",
  },
];

export default defineComponent({
  name: "MainLayout",

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});

// document.querySelector("#codeNom").addEventListener("q-input", function () {
//   if (this.value.length > 0) {
//     let url =
//       "https://api-dev.customsbridge.fr/get_ebti?limit=100&language=fr&filter_on_code=${this.value}";
//     fetch(url).then((response) =>
//       response.json().then((data) => console.log(data))
//     );
//   }
// });
</script>
