<script>
	/** @type {import('./$types').PageData} */
	import CommentBook from '$lib/components/book/CommentBook.svelte';
	import Icon from '@iconify/svelte';
</script>

<div class="w-full h-full">
	<div class="w-full bg-black h-12 flex pl-2 items-center">
		<Icon icon="pajamas:chevron-left" color="white" style="font-size: 35px" />
		<p class="font-semibold">All Comments</p>
	</div>
	<div class="p-4 mt-4">
		<CommentBook />
		<CommentBook />
		<CommentBook />
		<CommentBook />
		<CommentBook />
		<CommentBook />
		<CommentBook />
	</div>
</div>
