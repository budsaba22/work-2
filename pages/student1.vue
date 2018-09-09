<template>
<v-app>
  
   <v-form v-model="valid">
    <v-text-field
      v-model="name"
      :rules="nameRules"
      :counter="10"
      label="Name"
      required
    ></v-text-field>
    <v-text-field
      v-model="email"
      :rules="emailRules"
      label="E-mail"
      required
    ></v-text-field>
  </v-form>
    <div class="text-xs-center">
    <nuxt-link to="/table"><v-btn color="primary" dark><v-icon>lock_open</v-icon> </v-btn></nuxt-link>
    <nuxt-link to="/"><v-btn color="primary" dark><v-icon>power_settings_new</v-icon> </v-btn></nuxt-link>
  </div>
  <v-footer class="blue lighten-4">
    <v-spacer></v-spacer>
    <div>&copy; {{ new Date().getFullYear() }}</div>
  </v-footer>
  </v-app>
</template>

<script>
  export default {
    layout : "publics",
    data: () => ({
      valid: false,
      name: '',
      nameRules: [
        v => !!v || 'Name is required',
        v => v.length <= 10 || 'Name must be less than 10 characters'
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
      ]
    })
  }
</script>