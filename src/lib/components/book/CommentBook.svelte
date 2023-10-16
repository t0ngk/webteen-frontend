<script>
	import Icon from '@iconify/svelte';
</script>

<div class="w-full h-32 mb-4">
	<div class="flex flex-row items-center">
		<div class="w-8 h-8 bg-gray-200 rounded-full" />
		<h1 class="text-sm font-semibold ml-2">User1</h1>
		<Icon icon="la:award" color="white" style="font-size: 25px" class="ml-2" />
		<p class="text-sm text-gray-400 ml-1 flex-grow">3 Feb 2023</p>
		<div class="items-center mt-4">
			<Icon icon="ph:dot-bold" color="white" style="font-size: 25px" class="ml-2 -mt-5" />
			<Icon icon="ph:dot-bold" color="white" style="font-size: 25px" class="ml-2 -mt-5" />
			<Icon icon="ph:dot-bold" color="white" style="font-size: 25px" class="ml-2 -mt-5" />
		</div>
	</div>
	<p class="line-clamp-2 ml-8 text-xs mt-1 pr-3">
		Lorem ipsum, dolor sit amet consectetur adipisicing elit. Eaque mollitia cumque quibusdam
		similique error fugit eveniet non. Ab, nihil, perspiciatis inventore quibusdam, deleniti quos
		quaerat iusto ipsa necessitatibus eius qui!
	</p>
	<div class="flex flex-row items-center pr-3 mt-4">
		<p class="text-sm text-gray-400 ml-8 flex-grow">5 reply</p>
		<Icon icon="iconamoon:like" color="white" style="font-size: 20px" class="" />
		<p class="text-sm ml-1">621</p>
		<Icon icon="iconamoon:like" color="white" style="font-size: 20px" class="ml-1" />
		<p class="text-sm ml-1">4</p>
	</div>
	<div class="border border-white opacity-20 my-3" />
</div>
