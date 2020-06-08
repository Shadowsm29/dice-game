<template>
	<div class="game-container">
		<div class="players-container">
			<player :player="players[0]" />
			<player :player="players[1]" />
		</div>
		<buttons :dice-number="diceNumber" :is-game-in-porgress="isGameInPorgress" @new-game="newGame" @roll-dice="rollDice" @hold="hold" />
	</div>
</template>

<script>
export default {
	components: {
		Player: require("@/components/players/Player").default,
		Buttons: require("@/components/buttons/Buttons").default
	},

	data() {
		return {
			players: [
				{
					id: 1,
					active: true,
					winner: false,
					totalScore: 0,
					currentScore: 0
				},
				{
					id: 2,
					active: false,
					winner: false,
					totalScore: 0,
					currentScore: 0
				}
			],
			activePlayer: 0,
			diceNumber: 0,
			isGameInPorgress: true
		};
	},

	methods: {
		newGame() {
			this.isGameInPorgress = true;
			this.diceNumber = 0;

			this.players.forEach(player => {
				player.active = false;
				player.winner = false;
				player.currentScore = 0;
				player.totalScore = 0;
			});

			this.players[0].active = true;
		},
		rollDice() {
			if (!this.isGameInPorgress) return;

			this.diceNumber = Math.floor(Math.random() * 6) + 1;

			if (this.diceNumber === 1) {
				this.switchPlayer();
				return;
			}

			this.players[this.activePlayer].currentScore += this.diceNumber;
		},
		hold() {
			if (!this.isGameInPorgress) return;
			if (this.players[this.activePlayer].currentScore == 0) return;

			this.players[this.activePlayer].totalScore += this.players[
				this.activePlayer
			].currentScore;

			if (this.players[this.activePlayer].totalScore >= 20) {
				this.winGame();
				return;
			}

			this.switchPlayer();
		},
		switchPlayer() {
			const prevPlayer = this.players[this.activePlayer];
			prevPlayer.currentScore = 0;
			prevPlayer.active = false;

			this.activePlayer === 0 ? (this.activePlayer = 1) : (this.activePlayer = 0);

			const nextPlayer = this.players[this.activePlayer];
			nextPlayer.active = true;
		},
		winGame() {
			this.isGameInPorgress = false;
			this.players[this.activePlayer].winner = true;
			this.diceNumber = 0;

			this.players.forEach(player => {
				player.active = false;
				player.currentScore = 0;
			});
		}
	}
};
</script>

<style scoped>
.game-container {
	min-width: 800px;
	width: 800px;
	height: 500px;
	background-color: white;
	box-shadow: 0 0 21px 0px rgba(0, 0, 0, 0.6);
	position: relative;
}

.players-container {
	width: 100%;
	height: 100%;
	display: flex;
}
</style>