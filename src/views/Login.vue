<template>
  <v-container fill-height fluid>
    <v-row align="center" justify="center">
      <v-card width="400">
        <h1 class="textHead">Attendance</h1>
        <h3 class="textSub">App Tracking</h3>
        <v-card-text>
          <v-form @submit.prevent="onSubmit">
            <v-text-field
              label="Username"
              v-model="account.username"
              auto-grow
              outlined
              autofocus
            />
            <v-text-field
              :type="isShowPassword ? 'text' : 'password'"
              label="Password"
              v-model="account.password"
              auto-grow
              outlined
              :append-icon="isShowPassword ? 'visibility' : 'visibility_off'"
              @click:append="isShowPassword = !isShowPassword"
            />
            <v-row class="mb-3 px-5" justify="end">
              <router-link to="/forgot">
                <span>Forgot password?</span>
              </router-link>
              <br />
            </v-row>
            <v-row class="justify-space-between">
              <v-btn text class="ma-2" @click="$router.push('/register')"
                >register</v-btn
              >
              <v-btn type="submit" class="ma-2" color="yellow">login</v-btn>
            </v-row>
          </v-form>
        </v-card-text>
      </v-card>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      isShowPassword: false,
      account: {
        username: "",
        password: ""
      },
    };
  },
  methods: {
    onSubmit() {
      this.$router.push("/check-in");
      this.$store.dispatch({
        type: "DO_LOGIN",
        username: this.account.username,
        password: this.account.password,
      });
    },
  },
};
</script>

<style scoped>
.textHead {
  text-align: center;
  margin-bottom: 0;
  padding-bottom: 0;
  font-size: 50px;
  text-transform: uppercase;
}
.textSub {
  text-align: end;
  font-weight: 400;
  padding-top:0;
  padding-right: 50px;
  margin-top: 0;
}
</style>