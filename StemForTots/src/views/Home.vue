<template>
  <div class="index">
	
	<div class="tContainer">

		<div class="question">

			<h1>Question Goes Here</h1>
			<br />
		</div>

		<div class="answers">
			<b-button variant="primary" id="1"> 1st Option </b-button>

			<b-button variant="primary" id="2"> 2nd Option </b-button>

			<b-button variant="primary" id="3"> 3rd Option </b-button>

			<b-button variant="primary" id="4"> 4th Option </b-button>
		</div>
	</div>

	<div class="footer">
		
	</div>


  </div>
</template>




<style lang="scss">

.index {
    height: 100vh;
    margin: 0 auto;
}

    body {
        display: block;
        font-family: sans-serif;
        background: linear-gradient( #0caadc, #00ffb1);
        color: black;
        margin: 0 auto;
    }


.footer {
	position: fixed;
	background-color: darkslategray;
	height: 60px;
	width: 100%;
	bottom: 0;
}

.tContainer {
	display: inline-block;
	border-radius: 25px;
	width: 40%;
	padding: 10px 10px;
	margin: 100px auto;
	background-color: white;
	align-content: center;
	box-shadow: 0 0 8px blue;
}

.question {
	text-align: center;
}

.answers button{
	
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
