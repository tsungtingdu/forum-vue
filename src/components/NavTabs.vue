<template>
  <ul class="nav nav-tabs mb-4">
    <li v-for="tab in tabs" :key="tab.id" class="nav-item">
      <router-link :to="tab.path" class="nav-link">{{ tab.title }}</router-link>
    </li>
  </ul>
</template>

<script>
import uuid from "uuid/v4";
export default {
  data() {
    return {
      tabs: [
        {
          id: uuid(),
          title: "Main",
          path: "/restaurants"
        },
        {
          id: uuid(),
          title: "Latest activities",
          path: "/restaurants/feeds"
        },
        {
          id: uuid(),
          title: "Top 10 Restaurants",
          path: "/restaurants/top"
        },
        {
          id: uuid(),
          title: "Top 10 Users",
          path: "/users/top"
        }
      ]
    };
  }
};
</script>