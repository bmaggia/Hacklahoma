<template>
  <div>
      <div id="tContainer">
          <h3><b>Leaderboard</b></h3>

      </div>
  </div>
</template>

<script>


    import { db } from '../main.js';


    export default {
        Mounted() {
            this.getLeaderboard();
        },
        methods: {
            getLeaderboard() {

                db.collection("users").get().then( (snapshot) => {

                    snapshot.docs.forEach(doc => {
                        console.log(doc);
                    });
                });
            }
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
        width: 600px;
        padding: 10px 10px;
        margin: 0 auto;
        background-color: white;
        align-content: center;
        box-shadow: 0 0 4px blue;
    }
</style>