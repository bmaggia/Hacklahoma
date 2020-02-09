<template>
  <div>
    <div class="error" v-if="error">{{error.message}}</div>
    
    <form @submit.prevent="pressed">
        <div class="form-group">

            Register
            <div class="email">
                <input type="email" v-model="email" placeholder="email" />
            </div>
            <div class="password">
                <input type="password" v-model="password" placeholder="password" />
            </div>
            <button type="submit">Register</button>

        </div>

    </form>
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
        .createUserWithEmailAndPassword(this.email, this.password)
        .then(() => {
          console.log("here");
          this.$router.replace({ name: "secret" });
        })
        .catch(error => (this.error = error));
    }
  }
};
</script>


<style lang="scss">
    body {
        display: block;
        font-family: tahoma;
        background: linear-gradient( #0caadc, #00ffb1);
        height: 90vh;
        color: black;
        margin: 2px;
    }

    .nav-bar {
        background: linear-gradient(-90deg, #84CF6A, #16C0B0);
        height: 60px;
    }

    .footer {
        position: fixed;
        background: linear-gradient(-90deg, #84CF6A, #16C0B0);
        height: 60px;
        width: 100%;
        bottom: 0;
    }

    #tContainer {
        display: block;
        border-radius: 25px;
        width: 15%;
        padding: 10px 10px;
        margin: 0 auto;
        background-color: white;
        align-content: center;
        box-shadow: 0 0 4px blue;
    }

    .question {
        text-align: center;
    }

    .answers button {
        padding: 10px 24px;
        display: block;
        margin: 5px auto;
    }

    button {
        margin-top: 5px;
        border: none;
        border-radius: 25px;
        background-color: #1E95EA;
        color: white;
        height: 40px;
        width: 90%;
        font-size: 14px;
    }
</style>