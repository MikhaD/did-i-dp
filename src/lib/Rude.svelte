<script lang="ts">
	export let option: number;
</script>

{#if option == 0}
	<h2>The only DP you got is DePression</h2>
{:else if option == 1}
	<h2>The only DP you got is DisaPpointment</h2>
{/if}
