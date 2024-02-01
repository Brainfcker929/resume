<template>
  <v-sheet
    color="grey-lighten-4"
  >
    <v-img
      aspect-ratio="1/1"
      width="300"
      :src="profile.pictureSrc"
    />
    <v-card 
      :title="profile.name"
      :subtitle="profile.job"
      :text="profile.description"
      variant="outlined"
    />
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse</p>
  </v-sheet>
</template>

<script setup lang="ts">
import profilePic from "@/assets/pictures/me.png";


const profile = {
  pictureSrc: profilePic,
  name: "Paul Rusch",
  job: "Software En",
  description: "",
};
</script>