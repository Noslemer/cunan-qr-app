<template>
    <div class="d-flex align-center justity-center" style="height: 100vh;">
      <v-card width="500" elevation="10" class="pa-4">
            <v-card-text>
            <v-form>
                <v-text-field
                 outlined
                 label=" Email"
                ></v-text-field>
                <v-text-field
                 label=" Password"
                 outlined
                 type=" password"
                 prepend-inner-icon="mdi-lock"
                ></v-text-field>
            </v-form>
        </v-card-text>
        <v-card-actions class="pt-4">
            <v-btn color="blue dakrken-2" block large dark>Sign In</v-btn>
        </v-card-actions>
      </v-card>
    </div>
</template>
<script>
export default {
    layout: "auth"
}
</script>