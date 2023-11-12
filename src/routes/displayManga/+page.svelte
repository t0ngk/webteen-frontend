<script>
	import Icon from '@iconify/svelte';
	import { bookStore } from '../../stores/myStore';
	import { goto } from '$app/navigation';
	import { Button } from 'flowbite-svelte';
	import DisplayManga from '../../lib/components/writing/display/DisplayManga.svelte';
	import DisplayNovel from '../../lib/components/writing/display/DisplayNovel.svelte';

	let book;
	bookStore.subscribe((value) => {
		book = value;
	});
	// console.log(book);
</script>

<div class="container mt-5 relative">
	<div class="flex items-center justify-between p-2">
		<div class="flex gap-3 items-center">
			<button
				on:click={() => {
					goto('/manageWriting');
				}}
			>
				<Icon icon="ion:chevron-back" color="white" class="text-[30px]" />
			</button>
			<p class="text-[20px] font-semibold text-center flex-grow">EP1</p>
		</div>
		<Button
			class="w-auto mr-2 px-4 py-[3px] rounded-[5px] bg-[#F7B155] flex items-center gap-1"
			on:click={() => {
				//
			}}
		>
			<p class="text-black text-[12px] font-medium">Save</p>
		</Button>
	</div>

	<div>
		{#if book.category === 'Novel'}
			<DisplayNovel />
		{:else}
			<DisplayManga />
		{/if}
	</div>
</div>
