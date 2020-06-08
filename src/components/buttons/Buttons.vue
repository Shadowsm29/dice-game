<template>
	<div class="button-container">
		<div class="new-game-container">
			<button class="new-game-btn" @click="$emit('new-game')">
				<plus-icon class="btn-icon" />New Game
			</button>
		</div>
		<div>
			<img v-if="diceNumber > 0" :src="require(`@/assets/dice-${diceNumber}.png`)" :alt="`Dice rolled: ${diceNumber}`" class="dice" />
		</div>
		<div class="roll-hold-container">
			<button class="mb-3" @click="$emit('roll-dice')">
				<auto-renew-icon class="btn-icon" />Roll Dice
			</button>
			<button @click="$emit('hold')">
				<download-icon class="btn-icon" />Hold
			</button>
		</div>
	</div>
</template>

<script>
import PlusIcon from "vue-material-design-icons/Plus";
import AutoRenewIcon from "vue-material-design-icons/Autorenew";
import DownloadIcon from "vue-material-design-icons/Download";

export default {
	components: {
		PlusIcon,
		AutoRenewIcon,
		DownloadIcon
	},

	props: ["diceNumber", "isGameInPorgress"],

};
</script>

<style scoped>
.button-container {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: space-between;
}

button {
	font-family: "LatoThin";
	cursor: pointer;
	text-transform: uppercase;
	font-size: 20px;
	display: block;
   background-color: transparent;
   border: none;
   transition: all .2s linear;
   font-weight: 600;
}

button:focus {
   outline: none;
}

button:hover {
   transform: scale(1.03);
   
}

.new-game-container {
	margin-top: 50px;
}

.roll-hold-container {
   display: flex;
   flex-direction: column;
   align-items: center;
	margin-bottom: 100px;
}

.btn-icon {
	margin-right: 10px;
	color: #e17a84;
}

.dice {
   width: 120px;
   box-shadow: 0 0 20px 5px rgba(0, 0,0, .2);
}
</style>