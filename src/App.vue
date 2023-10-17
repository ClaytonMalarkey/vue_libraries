<template>
  <div id="app">
    <!-- Remove any HelloWorld references -->
    <AllUsers /> <!-- Add this line to use the AllUsers component -->
  </div>
</template>

<script>
import AllUsers from "@/components/AllUsers.vue"; // Import the AllUsers component

export default {
  name: "App",
  components: {
    AllUsers, // Register the AllUsers component for use in the template
  },
};
</script>