<script>
	/** @type {import('./$types').PageData} */
	export let data;
	import CommentBook from '$lib/components/book/CommentBook.svelte';
	import Recommend from '$lib/components/book/Recommend.svelte';

	import Icon from '@iconify/svelte';
</script>

<div class="w-full h-full">
	<div class="w-full bg-black h-12 flex pl-3 items-center">
		<Icon icon="uiw:menu" color="white" style="font-size: 25px" />
	</div>
	<div class="w-full h-5/6 bg-gray-300">content</div>
	<!-- navigate under content -->
	<div class="w-full h-10 bg-gray-700 flex items-center pl-3">
		<div class="flex flex-row flex-grow">
			<Icon icon="ph:heart-bold" color="white" style="font-size: 20px" />
			<p style="font-size: 14px" class="ml-1">3.2 k</p>
			<Icon icon="gg:comment" color="white" style="font-size: 20px" class="ml-2" />
			<p style="font-size: 14px" class="ml-1">30</p>
		</div>
		<div class="flex flex-row items-center">
			<p>#98</p>
			<Icon icon="pajamas:chevron-right" color="white" style="font-size: 35px" />
		</div>
	</div>
	<div class="pl-3">
		<h1 class="text-xl font-medium mt-4">Recommend</h1>
		<div class="flex flex-row gap-1 mt-3">
			<Recommend />
		</div>
		<!-- comment -->
		<h1 class="text-xl font-medium mt-4">Top comment</h1>
		<div class="p-3 mt-4">
			<CommentBook />
			<CommentBook />
			<CommentBook />
		</div>
	</div>
</div>
