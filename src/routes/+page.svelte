<script>
	import Recommend from '$lib/components/book/Recommend.svelte';
	import Icon from '@iconify/svelte';
</script>

<div class="h-full w-full">
	<div class="bg-gray-700 w-full h-72">
		<Icon
			icon="ic:sharp-search"
			color="#F7B155"
			style="font-size: 30px"
			class="absolute top-3 right-3"
		/>
		<!-- <img
			src="https://cdn.discordapp.com/attachments/895533055928852502/1162025735574278255/14517729691676530064.png?ex=653a6fcc&is=6527facc&hm=2081917ce025af5a2012a82945311342e79ae89eceea5ad6eb50ef3fd4277fef&"
			alt=""
			class="w-full h-full object-cover"
		/> -->
	</div>
	<h1 class="text-lg font-semibold py-3 p-3">Recommend for you</h1>
	<div class="h-full w-full flex justify-center">
		<div class="flex flex-row gap-3">
			<Recommend />
		</div>
	</div>
</div>
