<script>
	import Icon from '@iconify/svelte';
	import { fade } from 'svelte/transition';
	const carouselPhotos = [
		'https://picsum.photos/300/200?random=1',
		'https://picsum.photos/300/200?random=2',
		'https://picsum.photos/300/200?random=3'
	];

	let index = 0;
	const next = () => {
		index = (index + 1) % carouselPhotos.length;
	};
	const back = () => {
		index = (index - 1) % carouselPhotos.length;
	};
</script>

<div class="bg-gray-700 w-full h-72 flex justify-end items-center">
	{#each [carouselPhotos[index]] as src (index)}
		<img transition:fade {src} alt="" class="object-cover h-72 w-full absolute" />
	{/each}
	<div class="absolute top-3 right-3 flex justify-center items-center">
		<Icon
			icon="ic:sharp-search"
			color="#F7B155"
			style="font-size: 30px"
			class="absolute opacity-100"
		/>
		<div class="h-10 w-10 rounded-full bg-black bg-opacity-50" />
	</div>
	<button on:click={next} class="absolute">
		<Icon icon="pajamas:chevron-right" color="white" style="font-size: 35px" />
	</button>
	<div class="flex justify-start items-center w-full h-72">
		<button on:click={back} class="absolute">
			<Icon icon="pajamas:chevron-left" color="white" style="font-size: 35px" />
		</button>
	</div>
</div>
