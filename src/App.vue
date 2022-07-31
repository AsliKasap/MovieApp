<template>
  <div class="container" style="width=100%">
    <Navbar />
    <router-view />
  </div>
</template>


<script>

import Navbar from "./components/Navbar";

export default {
  components: {
    Navbar,
  },
};
</script>



