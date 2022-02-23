<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "@/components/HelloWorld.vue";
import { reactive, ref, defineComponent, computed } from "vue";

const author = reactive({
  labelVariable: "",
  posts: [
    {
      author: "@vFitzgerald",
      title: "Quod Ducimus Omnis",
      label: "science",
    },
    {
      author: "@mPalmer",
      title: "Vero Eius Laboriosam Ex Repudiandae",
      label: "math",
    },
    {
      author: "@mDean",
      title: "Magnam Odit",
      label: "science",
    },
    {
      author: "@tCole",
      title: "Velit Mollitia Voluptates Assumenda",
      label: "science",
    },
    {
      author: "@jCooper",
      title: "Eum Commodi Cupiditate",
      label: "poetry",
    },
  ],
});

// a computed ref
const publishedBooksMessage = computed(() => {
  console.log("a");
  return author.posts.filter((x) => x.label === author.labelVariable);
});
</script>

<template>
  <select v-model="author.labelVariable">
    <option disabled value="">Filter with a label</option>
    <option>science</option>
    <option>math</option>
    <option>poetry</option>
    <option>history</option>
  </select>

  <div v-for="post in publishedBooksMessage" :key="post.title" class="post">
    <span class="label">{{ post.label }}</span>
    <p>{{ post.title }}</p>
    <small>{{ post.author }}</small>
  </div>
</template>
