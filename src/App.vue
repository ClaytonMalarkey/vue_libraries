<template>
  <div id="app">
    <LoginForm />
    <AllUsers v-if="hasToken" />
  </div>
</template>

<script>
import LoginForm from "@/components/LoginForm.vue";
import AllUsers from "@/components/AllUsers.vue";

export default {
  name: "App",
  components: {
    LoginForm,
    AllUsers,
  },
  computed: {
    hasToken() {
      return document.cookie.split(";").some((c) => c.trim().startsWith("token="));
    },
  },
};
</script>
