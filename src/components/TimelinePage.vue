<template>
  <div>
    <h1>Timeline</h1>
    <v-timeline
      align="start"
      side="end"
      truncate-line="start"
    >
      <v-timeline-item
        v-for="(item, index) in items"
        :key="index"
        dot-color="cyan"
        :icon="item.icon"
        size="small"
      >
        <template #opposite>
          <div 
            class="pt-1 headline font-weight-bold text-cyan"
            v-text="item.year"
          />
        </template>
        <v-card
          class="max-auto"
          max-width="470"
        >
          <v-img
            src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
            height="200px"
            cover
          />
          <v-card-title>
            {{ item.title }}
          </v-card-title>
          <v-card-subtitle class="d-flex justify-space-between">
            <span>{{ item.company }}</span> 
            <span>{{ item.location }}</span>
          </v-card-subtitle>
          <v-spacer />
          <v-card-actions class="d-flex justify-end ">
            <v-btn
              color="red"
              :icon="item.show ? 'mdi-chevron-up' : 'mdi-chevron-down'"
              @click="toggle(item)"
            />
          </v-card-actions>
          <v-expand-transition>
            <div v-show="item.show">
              <v-divider />

              <v-card-text>
                <p>{{ item.description }}</p>
              </v-card-text>
            </div>
          </v-expand-transition>
        </v-card>
      </v-timeline-item>
    </v-timeline>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

type Item = {
  icon: string;
  title: string;
  company: string;
  location: string;
  year: string;
  description:string;
  show: boolean;
}

const toggle = (item: Item) => {
  item.show = !item.show;
};

const items = ref<Item[]>([
  {
    icon: "mdi-star",
    title: "FACHINFORMATIKER FÜR ANWENDUNGSENTWICKLUNG",
    company: "Telefonica Germany GmbH & Co. OHG",
    location: "Hamburg",
    year: "September 2019 - today",
    description: `Im Verlauf meiner Karriere habe ich erfolgreich verschiedene Projekte betreut.
Meine Verantwortlichkeiten umfassten Kundenprojekte bei Consente, wo ich mein Wissen in Node.js, TypeScript und Postgres vertiefen konnte. Besondere Kenntnisse im Umgang mit Vue habe ich
durch ein Microfrontend-Projekt erlangt, in dem wir Agenten
den Umzugsprozess und Vertragsverlängerungen erleichtert haben. Während meiner Ausbildung habe ich eine interne Webanwendung entwickelt, die Projektinformationen und KPIs visualisiert. Diese Leistung wurde mit dem Warp Award 2023 ausgezeichnet.
Weitere Details zum Warp Award 2023 sind hier verfügbar: http://bit.ly/warpAward2023`,
    show: false,
  },
  {
    icon: "mdi-book-variant",
    title: "HILFSKRAFT IM KLETTERZENTRUM",
    company: "Blau-Weiss Buchholz e.V.",
    location: "Buchholz", // TODO: verlinken nach Standort
    description: "Die Erfahrung in der Kletterhalle brachte mir bei, wie man Kunden in stressigen Situationen angemessen betreut und stets eine freundliche Ausstrahlung beibehält.",
    year: "Mai 2016 - Dezember 2023",
    show: false,
  },
  {
    icon: "mdi-airballoon",
    title: "AUSBILDUNG / FACHINFORMATIKER FÜR ANWENDUNGSENTWICKLER",
    company: "Berufliche Schule ITECH",
    location: "Wilhelmsburg", // TODO: verlinken nach Standort
    description: "In meiner Ausbildung als In meiner Ausbildung als Fachinformatiker für Anwendungsentwicklung erlernte ich vielfältige Ansätze zur Lösung von Softwareproblemen. Frühzeitig konnte ich eigenständig Projekte planen und direkten Kundenkontakt pflegen.Fachinformatiker für Anwendungsentwicklung erlernte ich vielfältige Ansätze zur Lösung von Softwareproblemen. Frühzeitig konnte ich eigenständig Projekte planen und direkten Kundenkontakt pflegen.",
    year: "September 2019 - Januar 2021",
    show: false,
  },
  {
    icon: "mdi-layers-triple",
    title: "ALLGEMEINE HOCHSCHULREIFE",
    company: "BBS Buchholz, Gesundheit und Medizin",
    location: "Buchholz", // TODO: verlinken nach Standort
    description: "TODO",
    year: "August 2014 - Juni 2018",
    show: false,
  },
]);
</script>