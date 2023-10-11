<script>
	import DrawerNavigation from './DrawerNavigation.svelte';
	let openDrawer = false;
</script>

<DrawerNavigation bind:open={openDrawer} />
<div class="flex">
	<!-- Triple bar svg -->
	<div class="flex-none w-50 h-14 ... z-10 mt-2">
		<button on:click={() => openDrawer = true}>
			<div>
				<svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 60 60">
					<rect width="40" height="4" rx="2.5" ry="2.5" fill="#98A2B3" />
					<rect y="15" width="40" height="4" rx="2.5" ry="2.5" fill="#98A2B3" />
					<rect y="30" width="40" height="4" rx="2.5" ry="2.5" fill="#98A2B3" />
				</svg>
			</div>
		</button>
	</div>
	<!-- Search bar -->
	<div class="flex-1 ...">
		<form>
			<div class="relative mt-1 ml-2 mr-3">
				<div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
					<svg
						class="w-5 h-5 text-gray-500 dark:text-gray-400"
						aria-hidden="true"
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 20 20"
					>
						<path
							stroke="currentColor"
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"
						/>
					</svg>
				</div>
				<input
					type="search"
					id="default-search"
					class="block w-full p-2 pl-28 text-sm text-white border-['#344054'] bg-[#292932] rounded-lg"
					required
				/>
			</div>
		</form>
	</div>
	<!-- Noti -->
	<div class="flex-none w-14 h-14 ...">
		<div class="relative mt-2 mr-4">
			<div
				class="absolute bottom-auto left-auto right-0 top-0 inline-block -translate-y-1/2 translate-x-2/4 rotate-0 skew-x-0 skew-y-0 scale-x-50 scale-y-50 rounded-full bg-pink-700 p-2.5 text-xs"
			/>
			<div>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 24 24"
					fill="currentColor"
					class="h-7 w-7"
				>
					<path
						fill-rule="evenodd"
						d="M5.25 9a6.75 6.75 0 0113.5 0v.75c0 2.123.8 4.057 2.118 5.52a.75.75 0 01-.297 1.206c-1.544.57-3.16.99-4.831 1.243a3.75 3.75 0 11-7.48 0 24.585 24.585 0 01-4.831-1.244.75.75 0 01-.298-1.205A8.217 8.217 0 005.25 9.75V9zm4.502 8.9a2.25 2.25 0 104.496 0 25.057 25.057 0 01-4.496 0z"
						clip-rule="evenodd"
					/>
				</svg>
			</div>
		</div>
	</div>
</div>
