<script>
	import Icon from '@iconify/svelte';

	/** @type {import('./$types').PageData} */
	export let data;
	let fileName = 'No file chosen';
</script>

<div class="flex w-full p-2 items-center pt-5 mb-4">
	<div class="flex-1 flex items-center">
		<button>
			<Icon icon="mdi:chevron-left" class="text-4xl" />
		</button>
	</div>
	<div class="flex-1 text-center text-xl">Info Creator</div>
	<div class="flex-1" />
</div>

<div class="w-full flex justify-center">
	<div class="w-9/12 grid gap-4">
		<div>
			<p class="text-xs">Pseudonym</p>
			<input type="text" class="border-b bg-transparent w-full p-1" placeholder="Pseudonym" />
		</div>
		<div>
			<p class="text-xs">Firstname</p>
			<input type="text" class="border-b bg-transparent w-full p-1" placeholder="Firstname" />
		</div>
		<div>
			<p class="text-xs">Lastname</p>
			<input type="text" class="border-b bg-transparent w-full p-1" placeholder="Lastname" />
		</div>
		<div>
			<p class="text-xs">ID Card</p>
			<input type="text" class="border-b bg-transparent w-full p-1" placeholder="ID Card" />
		</div>
		<div class="flex items-center gap-2">
			<input type="file" class="hidden" id="file-input" on:change={(e) => {
                fileName = e.target.files[0]?.name || 'No file chosen'
            }} />
			<label
				for="file-input"
				class="cursor-pointer bg-gray-200 hover:bg-gray-300 p-2 rounded text-sm font-medium text-gray-700 flex items-center gap-2"
			>
                <span>
                    <Icon icon="mdi:image" class="text-xl" />
                </span>
				Add photo
			</label>
            <p class="flex-1 truncate">{fileName}</p>
		</div>
        <div>
			<p class="text-xs">Bank</p>
			<!-- <input type="text" class="border-b bg-transparent w-full p-1" placeholder="ID Card" /> -->
            <select class="border-b bg-transparent w-full p-1" name="" id="">
                <option value="kbank">kasikorn</option>
            </select>
		</div>
        <div>
			<p class="text-xs">Bank account number</p>
			<input type="text" class="border-b bg-transparent w-full p-1" placeholder="ID Card" />
		</div>
        <button class="w-full transition px-2 py-1 bg-[#F7B155] text-[#161218] hover:bg-[#e8a64f] active:bg-[#d29547] rounded">
            Upgrade
        </button>
	</div>
</div>
