<script>
	import Icon from '@iconify/svelte';
	import { page } from '$app/stores';
	export let chapter;
	export let bookId;
</script>

<a href="/category/detailBook/{bookId}/{chapter._id}">
	<div class="w-full h-16 border-b-0 flex flex-row">
		<div class="h-16 w-24 bg-gray-300">
			<img src={chapter.cover} alt="" class="w-28 h-full object-cover" />
		</div>
		<div class="p-2 flex-grow">
			<p class="text-sm ml-1">EP. {chapter.number} {chapter.title}</p>
			<div class="flex flex-row mt-1 ml-1">
				<Icon icon="ph:heart-bold" color="white" style="font-size: 11px" class="mt-1 mr-1 " />
				<p class="text-xs">3.2 k</p>
				<p class="text-xs ml-3 text-gray-400">2 days ago</p>
			</div>
		</div>
		<p class="text-sm text-gray-400 self-center mr-4">#100</p>
	</div>
</a>
