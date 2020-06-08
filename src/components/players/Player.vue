<template>
	<div class="player-container" :class="{ 'active-backgroung': player.active }">
		<total-score :player="player" />
		<current-score :current-score="player.currentScore" />
	</div>
</template>

<script>
export default {
	components: {
		"total-score": require("@/components/players/Score/TotalScore").default,
		"current-score": require("@/components/players/Score/CurrentScore").default
   },
   
   props: ["player"],
};
</script>

<style scoped>
.player-container {
	height: 100%;
	display: flex;
	flex-direction: column;
	justify-content: space-around;
	align-items: center;
   text-align: center;
   flex: 0 0 50%;
}

.active-backgroung {
   background-color: #F6F6F6;
}
</style>