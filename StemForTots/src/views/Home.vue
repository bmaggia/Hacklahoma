<template>
  <div class="index">
	
	<div class="nav-bar"></div>

	<div id="tContainer">

		<div class="question">

			<h1>{{ product }}</h1>
			<br />
		</div>

		<div class="answers">
			<b-button variant="primary" id="1"> 1st Option </b-button>

			<b-button id="2"> 2nd Option </b-button>

			<button id="3"> 3rd Option </button>

			<button id="4"> 4th Option </button>
		</div>
	</div>

	<div class="footer">
		Footer
	</div>


  </div>
</template>




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
	width: 40%;
	padding: 10px 10px;
	margin: 0 auto;
	background-color: white;
	align-content: center;
	box-shadow: 0 0 4px blue;
}

.question {
	text-align: center;
}

.answers button{
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
