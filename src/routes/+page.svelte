<script lang="ts">
	import Hand from '../components/Hand.svelte';
	import type { CardData } from '../types/types';

	const cardsData: CardData[] = [
		{
			title: 'Wizard1',
			description: 'Cool Wizard',
		},
		{
			title: 'Wizard2',
			description: 'Cool Wizard',
		},
		{
			title: 'Wizard3',
			description: 'Cool Wizard',
		},
	];
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<Hand {cardsData} playerIndex={0} />
<Hand {cardsData} playerIndex={1} />
<Hand {cardsData} playerIndex={2} />
<Hand {cardsData} playerIndex={3} />
