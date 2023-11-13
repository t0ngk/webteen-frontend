<script>
	import Icon from '@iconify/svelte';
	import { fade } from 'svelte/transition';
	const carouselPhotos = [
		'https://cdn.discordapp.com/attachments/1161362796643090582/1173461603522457682/onepiece100.jpg?ex=65640a48&is=65519548&hm=67da2de63085c03bef4c92b2e915a9b8f92eb467841409a48d6f15c4c1320b9d&',
		'https://cdn.discordapp.com/attachments/1161362796643090582/1173461603954462870/Surviving-as-an-Illegitimate-Princess.jpg?ex=65640a48&is=65519548&hm=2794fa5c33dec027d5897f5f76b2b3dc12fdaf66c4cc7de85441edfeb9a89978&',
		'https://media.discordapp.net/attachments/1161362796643090582/1173458493433458708/solo-leveling.jpg?ex=65640762&is=65519262&hm=b297152a6f73cb330acbdac5ebe159e198b627e70365a141b9350519496c13a0&=&width=200&height=272'
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
