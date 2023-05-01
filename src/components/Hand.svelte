<script lang="ts">
	import type { CardData } from '../types/types';
	import Card from './Card.svelte';

	export let cardsData: CardData[];
	export let playerIndex = 0;

	const getTransformByIndex = (index: number) => {
		switch (index) {
			case 0:
				return 'none;';
			case 1:
				return 'translate(-35vw, -35vh) rotate(90deg);';
			case 2:
				return 'translate(0, -70vh) rotate(180deg);';
			case 3:
				return 'translate(35vw, -35vh) rotate(-90deg);';
		}
	};

	const transform = getTransformByIndex(playerIndex);
</script>

<div class="hand" style="--transform: {transform}">
	{#each cardsData as cardProps, i}
		<Card {...cardProps} posX={i * 200} posY={0} isPlayable={playerIndex === 0} />
	{/each}
</div>

<style>
	.hand {
		position: absolute;
		left: 35vw;
		bottom: 0;
		width: 30vw;
		height: 30vh;
		transform: var(--transform);
	}
</style>
