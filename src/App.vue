<template>
  <div id="app">
    <div class="flex-container">
      <SideBar />
      <!-- TODO: implement preloader animation -->
      <LeftColumn />
      <RightColumn />
    </div>
  </div>
</template>

<script>

import LeftColumn from './components/columns/LeftColumn';
import RightColumn from './components/columns/RightColumn';
import SideBar from './components/columns/SideBar';

export default {
  name: 'App',
  components: { LeftColumn, RightColumn, SideBar },
  data() {
    return {
      allPosts: [],
      currentUserId: 1,
      currentUserPosts: [],
      loading: true,
      otherPosts: [],
      rawData: [],
      totalNumOfPosts: null,
    };
  },

  async created() {
    await this.$store.dispatch('getAllPosts');
  },
};
</script>

<style>

html {}
body {
  background-color: #2b2112;
  font-family: "Roboto", sans-serif;
  font-size: 16px;
  height: 100vh;
  overflow-y: hidden;
}
.flex-container {
  display: flex;
  flex-direction: row;
  height: 96vh;
  margin: 1rem;
}
</style>
