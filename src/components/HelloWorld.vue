<template>
<v-container fluid fill-height>
  <v-row justify="center" align="center">
    <v-col cols="6" xl="3">
      <v-card elevation="10">
        <v-card-title class=" info darken-1 white--text">
          Input validation
        </v-card-title>

        <v-card-text class="mt-8">
          <v-form
          ref="form"
          v-model="valid"

          >
            <v-text-field
              v-model="name"
              :counter="10"
              :rules="nameRules"
              label="name"
              append-icon="mdi-account-circle"
              required
              outlined
              dense
            ></v-text-field>

            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="email"
              append-icon="mdi-email"
              required
              outlined
              dense
            ></v-text-field>

            <v-text-field
              v-model="password"
              :rules="passwordlRules"
              label="new password"
              :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
              :type="showPassword ? 'text' : 'password'"
              @click:append="showPassword = !showPassword"
              required
              outlined
              dense
            ></v-text-field>

          </v-form>

        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn class="error" block >submit</v-btn>
        </v-card-actions>

      </v-card>

    </v-col>
  </v-row>
</v-container>

  
</template>

<script>
export default {
  data() {
    return {
      valid: true,
      showPassword: false,

      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 10) ||  'Name must be less than 10 characters',
      ],

      email: '',
      emailRules: [
        v => !!v || 'Email is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],

      password: '',
      passwordlRules: [
        v => !!v || 'Password is required',
        v => /[a-z]+/.test(v) || 'One lowercase letter required',
        v => /[A-Z]+/.test(v) || 'One uppercase letter required',
        v => /.{8,}/.test(v) || '8 characters minimum',
        v => /[0-9]+/.test(v) || 'One number required',
        v => /[#?!@$%^&*-]/.test(v) || 'One special character required',
      ]
    }
  }


}
</script>

<style>

</style>