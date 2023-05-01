<script lang="ts">
	export let title: string, description: string;
	export let posX = 0;
	export let posY = 0;
	export let isPlayable = true;

	let isMouseDown = false;
	let cursorPosX: number;
	let cursorPosY: number;

	const handleMouseDown = (event: MouseEvent) => {
		isMouseDown = true;
		cursorPosX = event.clientX;
		cursorPosY = event.clientY;
	};

	const handleMouseUp = () => {
		isMouseDown = false;
	};

	const handleMouseMove = (event: MouseEvent) => {
		if (isMouseDown && isPlayable) {
			posX += event.clientX - cursorPosX;
			posY += event.clientY - cursorPosY;
			cursorPosX = event.clientX;
			cursorPosY = event.clientY;
		}
	};
</script>

<div class="card" style="--theme-posX: {posX}; --theme-posY: {posY}" on:mousedown={handleMouseDown}>
	<img
		src="https://www.flutesloot.com/wp-content/uploads/2021/03/warforged_wizard_by_captdiablo_de2mwm8-pre.jpg"
		alt={title}
	/>
	<div class="title">{title}</div>
	<div class="description">{description}</div>
</div>

<svelte:window on:mouseup={handleMouseUp} on:mousemove={handleMouseMove} />

<style>
	.card {
		position: absolute;
		left: calc(var(--theme-posX) * 1px);
		top: calc(var(--theme-posY) * 1px);
		display: flex;
		flex-direction: column;
		width: 150px;
		height: 200px;
		padding: 4px;
		border-color: black;
		border-style: solid;
		border-width: 1px;
	}
	img {
		width: 100%;
		pointer-events: none;
		user-select: none;
	}
	.title {
		user-select: none;
	}
	.description {
		user-select: none;
	}
</style>
