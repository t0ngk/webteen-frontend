<script>
	import Icon from '@iconify/svelte';
	import { Button } from 'flowbite-svelte';
	import MultiSelect from 'svelte-multiselect';
	import { onMount } from 'svelte';
	import axios from 'axios';

	let title = '';
	let description = '';
	let category = '';
	let type = '';
	let cover = '';
	let fileinput;

	function fileSelect() {
		let image = fileinput.files[0];
		let reader = new FileReader();
		reader.readAsDataURL(image);
		reader.onload = (e) => {
			cover = e.target.result;
		};
	}

	let selected;
	const types = ['Romance', 'Comedy', 'Fantasy', 'Action', 'Horror'];

	const categories = ['Manga', 'Comic', 'Novel'];
	let active = categories[0];

	const handleCategoryClick = (item) => {
		category = item;
		// console.log(category);
	};

	const handleTitleInput = (event) => {
		title = event.target.value;
		// console.log(title);
	};

	const handleDescriptionInput = (event) => {
		description = event.target.value;
		// console.log(description);
	};

	const handleSelectedTypes = (event) => {
		type = event.detail.value;
		console.log('Selected Types: ', type);
	};

	const createBook = async () => {
		const formData = new FormData();
		formData.append('cover', cover);
		formData.append('title', title);
		formData.append('description', description);
		formData.append('category', category);
		formData.append('type', type);
		// console.log(formData);

		try {
			const res = await axios.post(`http://localhost:8082/book-service/createBook`, {
				title: title,
				description: description,
				category: category,
				type: type,
				cover: cover
			});
		} catch (error) {
			console.error('Error fetching books:', error);
		}
	};
</script>

<div class="flex flex-col">
	{#if cover}
		<div class="flex justify-center">
			<div class="relative w-36 h-24 rounded-[10px]">
				<img class="w-[150px] h-[100px] rounded-[10px]" src={cover} alt="cover" />
				<Button
					class="p-1 absolute bottom-1 right-2"
					on:click={() => {
						fileinput.click();
					}}
				>
					<Icon icon="bi:camera-fill" style="font-size: 14px" class="text-white" />
				</Button>
			</div>
		</div>
	{:else}
		<div class="flex justify-center">
			<div class="w-[150px] h-[100px] bg-gray-200 rounded-[10px] relative">
				<Button
					class="p-1 absolute right-2 bottom-1"
					on:click={() => {
						fileinput.click();
					}}
				>
					<Icon icon="bi:camera-fill" style="font-size: 14px" class="text-[#373739]" />
				</Button>
			</div>
		</div>
	{/if}

	<input
		style="display:none"
		type="file"
		accept=".jpg, .jpeg, .png"
		on:change={fileSelect}
		bind:this={fileinput}
	/>

	<div class="flex flex-col gap-4 mt-5">
		<div class="border-[1px] rounded-[5px] border-black w-full h-auto py-1 px-3 relative">
			<p class="title">Title</p>
			<input
				bind:value={title}
				on:input={handleTitleInput}
				class="input text-[14px]"
				type="text"
				id="title"
				name="title"
			/>
		</div>

		<div class="border-[1px] rounded-[5px] border-black w-full h-auto py-1 px-3 relative">
			<p class="title">Description</p>
			<textarea
				bind:value={description}
				on:input={handleDescriptionInput}
				class="input text-[12px]"
				id="des"
				name="des"
			/>
		</div>

		<div class="border-[1px] rounded-[8px] border-black w-full h-auto pt-3 pb-2 px-3 relative">
			<p class="title">Select Category</p>
			<div class="bg-gray-200 w-full flex rounded-[8px]">
				{#each categories as item}
					<Button
						class={`font-semibold text-[12px] w-full h-[26px] ${
							active == item ? 'text-white bg-[#373739]' : 'text-black'
						}`}
						on:click={() => {
							active = item;
							handleCategoryClick(item);
						}}>{item}</Button
					>
				{/each}
			</div>
		</div>

		<div class="border-[1px] rounded-[5px] border-black w-full h-auto py-1 px-3 relative">
			<p class="title">Select Type</p>
			<MultiSelect
				bind:selected
				options={types}
				--sms-border="0"
				--sms-focus-border="white"
				--sms-selected-bg="#373739"
				--sms-selected-text-color="white"
				--sms-font-size="12px"
				on:selectedChange={handleSelectedTypes}
			/>
		</div>

		<Button class="bg-[#373739] py-2 text-[12px] font-medium" on:click={createBook}
			>Add Writing</Button
		>
	</div>
</div>

<style>
	.title {
		position: absolute;
		top: -8px;
		font-size: 10px;
		font-weight: 500;
		background: white;
		color: #161218;
	}
	.input {
		width: 100%;
		height: 100%;
		font-weight: 700;
	}
	.input:focus {
		outline: none;
	}
</style>
