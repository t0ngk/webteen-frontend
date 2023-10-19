<script>
	import Daily from './analysis/Daily.svelte';
	import Monthly from './analysis/Monthly.svelte';
	import Yearly from './analysis/Yearly.svelte';
	export let tabs = 'dai';

	const selectTab = (tab) => {
		tabs = tab;
	};
</script>

<div class="h-full w-full p-2">
	<div class="flex w-full justify-center mt-7">
		<div
			class="grid gap-1 bg-[#373739] border-[#44444F] grid-cols-3 rounded-lg text-[#979797] p-1 w-5/6"
		>
			<button
				class="px-2 py-1 rounded-lg transition"
				class:selected={tabs == 'dai'}
				on:click={() => selectTab('dai')}>Daily</button
			>
			<button
				class="px-2 py-1 rounded-lg transition"
				class:selected={tabs == 'mon'}
				on:click={() => selectTab('mon')}>Monthly</button
			>
			<button
				class="px-2 py-1 rounded-lg transition"
				class:selected={tabs == 'yea'}
				on:click={() => selectTab('yea')}>Yearly</button
			>
		</div>
	</div>
</div>

<div class="w-full flex flex-col justify-center items-center">
	{#if tabs == 'dai'}
        <Daily />
    {/if}
    {#if tabs == 'mon'}
        <Monthly />
    {/if}
    {#if tabs == 'yea'}
        <Yearly />
    {/if}
</div>

<style lang="postcss">
	.selected {
		@apply bg-[#F7B155] text-[#161218] border-[#979797];
	}
</style>
