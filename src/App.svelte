<script lang="ts">
	import { dp } from "./dp";
	import Rude from "./lib/Rude.svelte";

	const MAX_LENGTH = 7;
	let input: string = "";

	type InputEvent = KeyboardEvent & {
		currentTarget: EventTarget & HTMLInputElement;
	};
	function filter(e: InputEvent) {
		if (e.key.charCodeAt(0) < 48 || e.key.charCodeAt(0) > 57) {
			e.preventDefault();
		}
		console.log(input);
	}
</script>

<h1>Did I DP?</h1>

<div class="enter">
	<div>Enter your PeopleSoft Number:</div>
	<input on:keypress={filter} type="text" id="emplid" maxlength={MAX_LENGTH} bind:value={input} />
</div>

{#if input.length == MAX_LENGTH}
	{#if input in dp}
		{#if dp[input] === 1}
			<h2>Congratulations you have DP! Good luck with your exams.</h2>
		{:else}
			<!-- <Rude option={Math.round(Math.random())} /> -->
			<h2>You currently don't have DP</h2>
			<p>You can email the TA to appeal or report missing marks.</p>
		{/if}
	{:else}
		<h2>The PeopleSoft number {input} is either invalid or not registered for CSC3003S.</h2>
	{/if}
{/if}

<style lang="scss">
	h1 {
		font-size: 5rem;
	}
	.enter {
		margin: auto;
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 2rem;
		max-width: 50rem;
		div {
			font-weight: bold;
			font-size: 2rem;
			color: var(--accent-0);
		}
		input {
			font-size: 2rem;
			font-family: "Courier New", Courier, monospace;
			letter-spacing: 1rem;
			width: 18rem;
			text-align: center;
		}
	}

	@media screen and (max-width: 70rem) {
		.enter {
			flex-direction: column;
			gap: 1rem;
		}
	}
</style>
