<script>
	/** @type {import('./$types').PageData} */
	import Episode from '$lib/components/book/Episode.svelte';
	import Icon from '@iconify/svelte';
</script>

<div class="h-full w-full">
	<div class="sticky top-0">
		<div class="bg-gray-600 w-full h-72 p-6 opacity-75 absolute">
			<div class="flex justify-between w-full">
				<Icon icon="pajamas:chevron-left" color="white" style="font-size: 35px" />
				<Icon icon="ph:heart-bold" color="white" style="font-size: 23px" />
			</div>

			<div class="pl-3">
				<p class="text-xs text-gray-200 mt-7">Type</p>
				<p class="text-xl font-medium">Comic Name</p>
				<p>lorwwnefwpoffesgneofwmic nernioj</p>
			</div>
		</div>
		<img
			src="https://cdn.discordapp.com/attachments/895533055928852502/1162025735574278255/14517729691676530064.png?ex=653a6fcc&is=6527facc&hm=2081917ce025af5a2012a82945311342e79ae89eceea5ad6eb50ef3fd4277fef&"
			alt=""
			class="w-full h-72 object-cover"
		/>
	</div>
	<!-- <div class="divide-y divide-white"> -->
	<Episode />
	<Episode />
	<Episode />
	<Episode />
	<Episode />

	<!-- </div> -->
</div>
