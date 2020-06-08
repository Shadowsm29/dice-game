<template>
	<div id="app">
		<router-view />
	</div>
</template>

<script>
export default {
	name: "App"
};
</script>

<style>
@font-face {
  font-family: 'Lato';
  src:  url('./fonts/Lato-Light.ttf') format('woff2');
}

@font-face {
  font-family: 'LatoThin';
  src:  url('./fonts/Lato-Thin.ttf') format('woff2');
}

#app {
	/* background-color: red; */
	height: 100vh;
	width: 100vw;
	display: flex;
	justify-content: center;
	align-items: center;
	background-image: url("./assets/back.jpg");
	background-size: cover;
	background-repeat: no-repeat;
	background-position: center center;
	font-family: Lato;
	font-weight: 1000;
	color: #555;
}
</style>