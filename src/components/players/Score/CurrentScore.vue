<template>
	<div class="score-container">
		<p class="title">Current</p>
		<h1 class="score">{{ currentScore }}</h1>
	</div>
</template>

<script>
export default {
   props: ["currentScore"]
};
</script>

<style scoped>
.score-container {
   background-color: #FF333E;
   padding: 5px 40px 5px 40px;
   text-transform: uppercase;
}

.score {
   color: white;
   margin: 0;
}

.title {
   font-size: 10px;
   margin: 0;
}
</style>