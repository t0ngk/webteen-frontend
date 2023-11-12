<script>
	import Icon from '@iconify/svelte';
	import { AccordionItem, Accordion } from 'flowbite-svelte';
	export let comment;

	const addReportComment = async () => {
		console.log('commentId ', comment.commentId)

		fetch(
			`http://localhost:8082/report-service/addReport/comment/${comment.commentId}`,
			{method: 'POST',
			body: '',
			redirect: 'follow'}
		)
			.then((response) => response.text())
			.then((result) => console.log(result))
			.catch((error) => console.log('error', error));
	};
</script>

<div class="w-full h-32 mb-4">
	<Accordion flush>
		<div class="flex flex-row items-center">
			<div class="w-8 h-8 bg-gray-200 rounded-full" />
			<h1 class="text-sm font-semibold ml-2 text-white">{comment.userId}</h1>
			<Icon icon="la:award" color="#F7B155" style="font-size: 25px" class="ml-2" />
			<p class="text-sm text-gray-400 ml-1 flex-grow">3 Feb 2023</p>
			<!-- ปุ่ม -->
			<button
				class="bg-[#C13E3E] text-white px-2 py-[1.5px] rounded-full"
				on:click={addReportComment}
				>Report
			</button>
			<!-- <div class="items-center mt-4" on:click={addReportComment}>
				<Icon icon="ph:dot-bold" color="white" style="font-size: 25px" class="ml-2 -mt-5" />
				<Icon icon="ph:dot-bold" color="white" style="font-size: 25px" class="ml-2 -mt-5" />
				<Icon icon="ph:dot-bold" color="white" style="font-size: 25px" class="ml-2 -mt-5" />
			</div> -->
		</div>
		<p class="line-clamp-2 ml-8 text-xs mt-1 pr-3 text-white">
			{comment.commentDetail}
		</p>
		<div class="flex flex-row items-center pr-3 mt-6 justify-end">
			<Icon icon="iconamoon:like" color="white" style="font-size: 20px" class="" />
			<p class="text-sm ml-1 text-white">621</p>
			<Icon icon="iconamoon:like" color="white" style="font-size: 20px" class="ml-3" />
			<p class="text-sm ml-1 text-white">4</p>
		</div>
		<AccordionItem class=" -mt-11 w-1/3 border-none">
			<div slot="header" class="w-full">
				<p class="text-sm text-gray-400 ml-8">5 reply</p>
			</div>

			<!-- reply comment -->
			<div class="ml-8 flex flex-row">
				<Icon
					icon="fa:angle-down"
					color="white"
					style="font-size: 20px; transform: rotate(45deg);"
					class=""
				/>
				<div class="rounded-md flex bg-[#373739] h-10 w-full ml-3">
					<textarea class="resize-none w-full rounded-md bg-[#373739] outline-none" />
					<Icon
						icon="fe:paper-plane"
						color="#F7B155"
						style="font-size: 30px"
						class="m-2 self-end"
					/>
				</div>
			</div>
		</AccordionItem>
	</Accordion>
	<!-- <div class="border border-white opacity-20 my-3" /> -->
</div>
