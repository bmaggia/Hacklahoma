<template>
  <div>
    <h3>Login</h3>
    <b-form @submit.prevent="pressed">
        
      <div class="login">
          <b-form-group label="Email address:">
              <b-form-input type="email" placeholder="login" v-model="email" />
          </b-form-group>
      </div>

      <div class="password">
          <b-form-group label="Password:">
              <b-form-input type="password" placeholder="password" v-model="password" />
          </b-form-group>
       </div>

      <b-button type="submit" variant="primary">Submit</b-button>

    <div class="error" v-if="error">{{error.message}}</div>
    </b-form>
  </div>
</template>

<script>
import * as firebase from "firebase/app";
import "firebase/auth";
export default {
  data() {
    return {
      email: "",
      password: "",
      error: ""
    };
  },
  methods: {
    pressed() {
      firebase
        .auth()
        .signInWithEmailAndPassword(this.email, this.password)
        .then(data => {
          console.log(data);
          this.$router.replace({ name: "secret" });
        })
        .catch(error => {
          this.error = error;
        });
    }
  }
};
</script>

