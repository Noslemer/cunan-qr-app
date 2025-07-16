<template>
  <div class="d-flex align-center justify-center" style="height: 100vh">
    <v-card width="500" elevation="10" class="pa-4">
      <v-card-text>
        <v-form>
          <v-text-field
            outlined
            label="Email"
            prepend-inner-icon="mdi-account"
          ></v-text-field>
          <v-text-field
            label="Password"
            outlined
            type="password"
            prepend-inner-icon="mdi-lock"
          ></v-text-field>
        </v-form>
      </v-card-text>

      <v-card-actions class="pt-4 d-flex flex-column">
        <!-- Regular Sign In Button -->
        <v-btn color="blue darken-2" block large dark> Sign In </v-btn>

        <!-- Spacer -->
        <div class="text-center my-2">
          <small class="text--secondary">or sign in with</small>
        </div>

        <!-- Google Sign-In Button -->
        <v-btn color="white" block large outlined @click="signInWithGoogle">
          <v-icon left> mdi-google </v-icon>
          Sign in with Google
        </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
export default {
  layout: "auth",
  middleware: "guest",
  methods: {
    signInWithGoogle() {
      this.$auth.loginWith("google");
    },
  },
};
</script>
