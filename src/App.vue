<template>
  <v-app>
    <v-app-bar
      density="compact"
      rounded
    >
      <v-app-bar-nav-icon active>
        Icon
      </v-app-bar-nav-icon>
      <v-toolbar-title text="Pauls Portfolio" />
      <v-btn
        icon="mdi-theme-light-dark"
        @click="toggleTheme"
      />
    </v-app-bar>
      
    <v-navigation-drawer location="right">
      <v-list-item title="Navigation" />
      <v-divider />
        
      <v-list
        density="compact"
        nav
      >
        <!-- wieso gehen icons nicht -->
        <v-list-item
          v-for="item in navigationItems"
          :key="item.title"
          :href="makeId(item.title)"
          :title="item.title"
          :prepend-icon="item.icon"
        />
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container>
        <v-row>
          <CoverPage id="Home" />
        </v-row>
        <v-row>
          <AboutPage id="About" />
        </v-row>
        <v-row>
          <TimelinePage id="Timeline" />
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
import CoverPage from "./components/CoverPage.vue";
import AboutPage from "./components/AboutPage.vue";
import TimelinePage from "./components/TimelinePage.vue";
import { useTheme } from "vuetify/lib/framework.mjs";

const theme = useTheme();
const toggleTheme = () => {
  theme.global.name.value = theme.global.current.value.dark ? "light" : "dark";
};

const navigationItems = [
  { title: "Home", icon: "mdi-home" },
  { title: "About", icon: "mdi-information" },
  { title: "Timeline", icon: "mdi-email" },
  { title: "Contact", icon: "mdi-email" },
];
const makeId = (title: string) => {
  return `#${title}`;
};
</script>
