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
      <!-- Formulaire permettant d'entrer code nomenclature et RTC -->
      <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
        <div class="row" filled>
          <q-icon name="format_size" style="color: #ccc; font-size: 2em" />
          <q-input
            @keydown.enter="enter()"
            v-model="text"
            label="Tapez votre code nomenclature"
            name="codeNom"
            style="width: 30%"
          />

          <q-input
            v-model="text2"
            label="Decrivez votre RTC"
            name="rtc"
            class="col offset-1"
          />

          <q-btn @click="enter" class="col-1 offset-1"> Entrer</q-btn>
        </div>
      </q-form>
      <!-- Fin du formulaire -->

      <!-- Début card -->
      <div class="fit row wrap justify-start items-start content-start">
        <q-card class="col my-card" style="width: 20%; margin-top: 5%">
          <q-card-section>
            <div class="row wrap">
              <div class="col-2">
                <img src="../assets/danemark.png" style="width: 30%" />
              </div>
              <div class="col">DK17-0806631</div>
              <div class="col offset-1">16/08/18</div>
            </div>
          </q-card-section>

          <q-separator />

          <q-card-actions vertical>
            <div>
              L'article est un outil électrique de type pistolet avec une
              cartouche adhésive insérée, également ap...
            </div>
          </q-card-actions>
          <img src="../assets/pistolet.jpeg" />
        </q-card>

        <q-card
          class="col my-card"
          style="width: 20%; margin-left: 5%; margin-top: 5%"
        >
          <q-card-section>
            <div class="row">
              <div class="col-2">
                <img src="../assets/danemark.png" style="width: 30%" />
              </div>
              <div class="col">DK17-0806631</div>
              <div class="col offset-1">16/08/18</div>
            </div>
          </q-card-section>

          <q-separator />

          <q-card-actions vertical>
            <div>
              L'article est un outil électrique de type pistolet avec une
              cartouche adhésive insérée, également ap...
            </div>
          </q-card-actions>
          <img src="../assets/pistolet.jpeg" />
        </q-card>

        <q-card
          class="col my-card"
          style="width: 20%; margin-left: 5%; margin-top: 5%"
        >
          <q-card-section>
            <div class="row">
              <div class="col-2">
                <img src="../assets/danemark.png" style="width: 30%" />
              </div>
              <div class="col">DK17-0806631</div>
              <div class="col offset-1">16/08/18</div>
            </div>
          </q-card-section>

          <q-separator />

          <q-card-actions vertical>
            <div>
              L'article est un outil électrique de type pistolet avec une
              cartouche adhésive insérée, également ap...
            </div>
          </q-card-actions>
          <img src="../assets/pistolet.jpeg" />
        </q-card>
      </div>
      <!-- Fin des cards -->
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
    const text = ref("");
    const text2 = ref("");

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
      text,
      text2,
    };
  },

  methods: {
    enter() {
      if (this.text > 0) {
        let url = `https://api-dev.customsbridge.fr/get_ebti?limit=100&language=fr&filter_on_code=${this.text}`;
        console.log("coucou");
        fetch(url).then(
          (response) => console.log(response),
          response.json().then((data) => console.log(data))
        );
      }
    },
  },
});
</script>
