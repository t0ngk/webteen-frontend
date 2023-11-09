<script>
	/** @type {import('./$types').PageData} */
	import CommentBook from '$lib/components/book/CommentBook.svelte';
	import Icon from '@iconify/svelte';
	import { AccordionItem, Accordion } from 'flowbite-svelte';
</script>

<div class="w-full h-full">
	<div class="w-full bg-black h-12 flex pl-2 items-center">
		<Icon icon="pajamas:chevron-left" color="white" style="font-size: 35px" />
		<p class="font-semibold">All Comments</p>
	</div>
	<div class="p-4">
		<div class="rounded-md flex bg-[#373739] h-20 w-full mb-5">
			<textarea class=" resize-none h-20 w-full rounded-md bg-[#373739] outline-none" />
			<Icon icon="fe:paper-plane" color="#F7B155" style="font-size: 30px" class="m-2 self-end" />
		</div>
			<CommentBook />
	</div>
</div>
