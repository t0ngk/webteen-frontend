<script>
	import Icon from '@iconify/svelte';
	import { goto } from '$app/navigation';
	import { Button } from 'flowbite-svelte';
	import { dndzone } from 'svelte-dnd-action';

	let images = [];
	let items = images;
	let fileinput;

	function fileSelect() {
		const selectedImages = fileinput.files;

		for (let i = 0; i < selectedImages.length; i++) {
			const image = selectedImages[i];
			let reader = new FileReader();
			reader.readAsDataURL(image);
			reader.onload = (e) => {
				const newId = items.length + 1;
				images.push({
					id: newId,
					name: image.name,
					url: e.target.result
				});
				items = images;
			};
		}
		// console.log(items);
	}

	function handleSort(e) {
		items = e.detail.items;
	}
</script>

<div>
	<div class="ml-4 mt-2 flex justify-between items-center">
		<Button
			class="border-[1px] rounded-[20px] px-4 py-2"
			on:click={() => {
				fileinput.click();
			}}
		>
			<Icon icon="ph:image" style="font-size: 16px" class="text-white" />
			<p class="ml-2 text-[12px] font-normal">Upload</p>
		</Button>
		<Button
			on:click={() => {
				images = [];
				items = images;
			}}
		>
			<Icon icon="majesticons:delete-bin-line" style="font-size: 16px" class="text-white" />
			<p class="ml-1 text-[12px] font-normal">Clear all</p>
		</Button>
	</div>
	<input
		style="display:none"
		type="file"
		accept=".jpg, .jpeg, .png"
		on:change={fileSelect}
		multiple
		bind:this={fileinput}
	/>

	<div class="w-full h-[41rem] bg-[#373739] mt-5">
		{#if items.length > 0}
			<div
				class="flex flex-wrap"
				use:dndzone={{ items }}
				on:consider={handleSort}
				on:finalize={handleSort}
			>
				{#each items as image (image.id)}
					<img class="m-1 w-[130px] relative" src={image.url} alt={image.name} />
				{/each}
			</div>
		{/if}
	</div>
</div>
