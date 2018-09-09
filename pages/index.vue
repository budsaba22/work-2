<template>
<v-parallax src="/image/123.jpg" >
  <div>
    <nuxt-link to="/student1">
    <center>
       <div class="text-xs-center">
    <v-btn round color="primary" dark>LOGIN</v-btn>
  </div>
    </center> 
    </nuxt-link><br>
    <router-link :to="{ path: '/Profile'}" replace><center>
      <div class="text-xs-center">
        <v-btn round color="primary" dark>PROFILE</v-btn>
      </div>
    </center>
    </router-link><br>
    <router-link :to="{ path: '/student2'}" push><center>Register</center></router-link><br>
  </div>

</v-parallax>

</template>

<script>
export default {
  layout : "public",
  data() {
    return {
      id: 1,
    }
  },
}
</script>