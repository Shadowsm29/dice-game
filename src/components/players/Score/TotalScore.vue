<template>
	<div>
		<h1 class="name">
			<span v-if="player.winner" class="winner-name">WINNER!</span>
			<span v-else>Player {{ player.id }}</span>
			<span class="circle-icon" v-if="player.active">
				<circle-icon />
			</span>
		</h1>
		<h1 class="score">{{ player.totalScore }}</h1>
	</div>
</template>

<script>
export default {
	components: {
		CircleIcon: require("vue-material-design-icons/CheckboxBlankCircle").default
	},

	props: ["player"]
};
</script>

<style scoped>
.name {
   display: flex;
   align-items: center;
	text-transform: uppercase;
}

.score {
	color: #e17a84;
	font-family: "LatoThin";
	font-size: 80px;
}

.circle-icon {
   margin-left: 10px;
   font-size: 15px;
   color: #E17A84;
}

.winner-name {
   color: #E17A84;
}
</style>