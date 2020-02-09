<template>
    <div>
        <div id="tContainer">
            <div v-if="ismember">
                <h3><b>Login</b></h3>
                <b-form @submit.prevent="pressed">
                    <b-container style="padding:20px">
                        <div class="login">
                            <b-form-input type="email" placeholder="login" v-model="email" />
                        </div>
                    </b-container>

                    <b-container style="padding:20px">
                        <div class="password">
                            <b-form-input type="password" placeholder="password" v-model="password" />
                        </div>
                    </b-container>

                    <b-button type="submit" variant="primary">Submit</b-button>

                    <div class="error" v-if="error">{{error.message}}</div>
                </b-form>

                <hr />
                <p>Not a member?</p>

                <b-button v-on:click="notUser">Sign Up!</b-button>

            </div>

            <div v-if="!ismember">
                <h3><b>Sign Up</b></h3>

                <b-form @submit.prevent="register">
                    <div class="login">
                        <b-container style="padding:20px">
                            <b-form-input type="email" placeholder="email addres" v-model="email" />
                        </b-container>
                    </div>
                    <div class="username">
                        <b-container style="padding:20px">
                            <b-form-input type="text" placeholder="username" v-model="username" />
                        </b-container>
                    </div>
                    <div class="password">
                        <b-container style="padding:20px">
                            <b-form-input type="password" placeholder="password" v-model="password" />
                        </b-container>
                    </div>


                    <b-button type="submit" variant="primary">Submit</b-button>

                    <div class="error" v-if="error">{{error.message}}</div>
                </b-form>
            </div>
            
        </div>
    </div>
</template>

<script>
    import { db } from '../main.js';

import * as firebase from "firebase/app";
import "firebase/auth";
export default {
        methods: {
        notUser() {
              this.ismember = false;
              console.log(this.ismember);
          }, // SIGNUP
        pressed() {
          firebase
            .auth()
            .signInWithEmailAndPassword(this.email, this.password)
            .then(data => {
              console.log(data);
              this.$router.replace({ name: "home" });
            })
            .catch(error => {
                this.error = error;
            });
        }, // REGISTER
        register() {
            firebase
                .auth()
                .createUserWithEmailAndPassword(this.email, this.password)
                .then(() => {
                    console.log("here");
                    this.$router.replace({ name: "secret" });
                })
                .catch(error => (this.error = error));


            db.collection("users").add({
                email: this.email,
                score: 0,
                username: this.username
            })
                .then(function (docRef) {
                    console.log("Document written with ID: ", docRef.id);
                })
                .catch(function (error) {
                    console.error("Error adding document: ", error);
                });
        }
    },
    data() {
    return {
      email: "",
      password: "",
      username: "",
      error: "",
      ismember: true
    };
  }
};
</script>

<style lang="scss">
    body {
        display: block;
        font-family: tahoma;
        background-color: bisque;
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

        width: 320px;
        padding: 10px 10px;
        margin: 0 auto;
        background-color: white;
        align-content: center;
        box-shadow: 0 0 4px blue;
    }

</style>