<script>
	import Icon from '@iconify/svelte';
	import { Button } from 'flowbite-svelte';
	import MultiSelect from 'svelte-multiselect';
	import { bookStore } from '../../../../stores/myStore';
	import axios from 'axios';

	let book;
	bookStore.subscribe((value) => {
		book = value;
	});
	// console.log(book._id);

	let number = '';
	let title = '';
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

	const handleTitleInput = (event) => {
		title = event.target.value;
		// console.log(title);
	};

	const handleNumberInput = (event) => {
		number = event.target.value;
		// console.log(number);
	};

	const createChapter = async () => {
		const formData = new FormData();
		formData.append('number', number);
		formData.append('title', title);
		formData.append('cover', cover);
		formData.append('bookId', book._id);

		try {
			const res = await axios.post('http://localhost:8082/book-service/createChapter', formData, {
				headers: {
					Authorization: `Bearer ${localStorage.getItem('accessToken')}`,
					'Content-Type': 'multipart/form-data'
				}
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
			<p class="title">Episode</p>
			<input
				class="input text-[14px]"
				type="text"
				id="number"
				name="number"
				bind:value={number}
				on:input={handleNumberInput}
			/>
		</div>

		<div class="border-[1px] rounded-[5px] border-black w-full h-auto py-1 px-3 relative">
			<p class="title">Name</p>
			<input
				class="input text-[14px]"
				type="text"
				id="title"
				name="title"
				bind:value={title}
				on:input={handleTitleInput}
			/>
		</div>

		<Button class="bg-[#373739] py-2 text-[12px] font-medium" on:click={createChapter}
			>Add Episode</Button
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
