<template>
    <div class="mainDiv">
        <div id="mySidebar" class="sidebar">
            <a href="javascript:void(0)" class="closebtn" v-on:click="closeNav()">×</a>
            <a href="/">Home</a>
            <a href="/about">About</a>
            <a href="/leaderboard">Leaderboard</a>
        </div>
        <nav id="main" class="header">
            <div class="menu-icon" v-on:click="openNav()" style="float:left">
                <div class="bar1"></div>
                <div class="bar1"></div>
                <div class="bar1"></div>
            </div>

            <div class="login" style="float:right">
                <button id="loginBtn" v-on:click="openLogin()">Login</button>
            </div>
        </nav>

        <div id="title">
        </div>
    </div>


</template>

<script>import * as firebase from "firebase/app";
    import "firebase/auth";
    export default {
        name: "top-header",
        mounted() {
            this.setupFirebase();
        },
        methods: {
            setupFirebase() {
                firebase.auth().onAuthStateChanged(user => {
                    if (user) {
                        // User is signed in.
                        console.log("signed in");
                        this.loggedIn = true;
                    } else {
                        // No user is signed in.
                        this.loggedIn = false;
                        console.log("signed out", this.loggedIn);
                    }
                });
            },
            signOut() {
                firebase
                    .auth()
                    .signOut()
                    .then(() => {
                        this.$router.replace({ name: "login" });
                    });
            },

             openNav() {
        document.getElementById("mySidebar").style.width = "250px";
        document.getElementById("main").style.marginLeft = "250px";
    },
     closeNav() {
        document.getElementById("mySidebar").style.width = "0";
        document.getElementById("main").style.marginLeft = "0";
            },
            openLogin() {
                this.$router.replace({ name: "login" });
            },
        },

        data() {
            return {
                loggedIn: false
            };
        }
    };</script>



<style lang="scss" scoped>


    .mainDiv {
        display:inline-block;
        padding-bottom: 50px;
    }

    .dropdown {
        font-size: 35px;
    }

    .header {
        padding-top:40px;
        padding-left: 40px;
        display: inline-block;
        position: fixed;
        width: 100%;
        left: 0;
        transition: .5s;
    }

    .menu-icon {
        display: inline-block;
        cursor: pointer;
    }

    #loginBtn {
        background-color: inherit;
        font-size: 30px;
        font-family: sans-serif;
        padding-right: 40px;
        margin: 0 auto;
        outline: none;
    }

    .bar1, .bar2, .bar3 {
        width: 35px;
        height: 5px;
        background-color: #FFFFFF;
        margin: 6px 0;
    }

    .sidebar {
        height: 100%;
        width: 0;
        position: fixed;
        z-index: 1;
        top: 0;
        left: 0;
        background-color: #111;
        overflow-x: hidden;
        transition: 0.5s;
        padding-top: 60px;
    }

    .sidebar a {
        padding: 8px 8px 8px 32px;
        text-decoration: none;
        font-size: 25px;
        color: #FFFFFF;
        display: block;
        text-align:left;
        font-family: sans-serif;
    }

    .sidebar a:hover {
        color: #F1F1F1;
    }

    .sidebar .closebtn {
        position: absolute;
        top: 0;
        right: 25px;
        font-size: 36px;
        margin-left: 50px;
    }

    .openbtn {
        font-size: 20px;
        cursor: pointer;
        background-color: #111;
        color: white;
        padding: 10px 15px;
        border: none;
    }

    .openbtn:hover {
        background-color: #444;
    }
</style>