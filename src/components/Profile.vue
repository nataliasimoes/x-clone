<script setup>
import { ref } from "vue";
import Tweet from "./Tweet.vue";
import Replies from "./Replies.vue";
import Media from "./Media.vue";
import Likes from "./Likes.vue";

const tab = ref(null);

const tabList = [
  { title: "Posts", value: "posts", component: Tweet },
  { title: "Replies", value: "replies", component: Replies },
  { title: "Media", value: "media", component: Media },
  { title: "Likes", value: "likes", component: Likes },
];
</script>

<template>
  <v-container class="w-50 pa-0">
    <v-img height="300" src="/vuemastery_header.png" cover></v-img>
    <v-container class="pa-0 px-6">
      <v-row justify="space-between" class="profile">
        <v-col cols="auto">
          <v-avatar image="/vuemastery_logo.png" size="200"></v-avatar>
        </v-col>
        <v-col cols="auto" class="mt-6" align-self="center">
          <v-btn variant="outlined" rounded="xl">Edit Profile</v-btn>
        </v-col>
      </v-row>
      <div class="pl-8">
        <h2 class="pt-4">Natália Simões</h2>
        <p>@nataliasimoes</p>

        <p class="py-2">
          I'm a software engineer who loves to learn and share knowledge. I'm
          passionate about technology and science, and I'm always looking for
          new challenges.
        </p>
      </div>

      <v-row class="pl-6 pt-6">
        <v-col class="d-flex" cols="auto">
          <v-icon icon="mdi-map-marker" class="mr-1" size="small"></v-icon>
          <span>Rio Grande do Norte, Brazil</span>
        </v-col>
        <v-col class="d-flex" cols="auto">
          <v-icon icon="mdi-calendar-month" class="mr-1" size="small"></v-icon>
          <span>Joined December, 2023</span>
        </v-col>
      </v-row>

      <v-row class="pl-6">
        <v-col cols="auto">
          <span><strong>567</strong> Following</span>
        </v-col>
        <v-col cols="auto">
          <span><strong>1,234</strong> Followers</span>
        </v-col>

      </v-row>

      <v-tabs class="pl-6 mt-3" v-model="tab" grow>
        <v-tab v-for="tab in tabList" :key="tab.value" :value="tab.value" color="blue">
          {{ tab.title }}
        </v-tab>
      </v-tabs>

      <v-window v-model="tab">
        <v-window-item v-for="tab in tabList" :value="tab.value" :key="tab.value">
          <component :is="tab.component" />
        </v-window-item>
      </v-window>
    </v-container>
  </v-container>
</template>

<style>
.profile {
  margin-top: -100px;
}
</style>
