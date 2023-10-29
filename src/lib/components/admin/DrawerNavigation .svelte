<script>
	import { Drawer, Button, CloseButton, Sidebar, SidebarWrapper } from 'flowbite-svelte';
	import { sineIn } from 'svelte/easing';
	import { goto } from '$app/navigation';
	import Icon from '@iconify/svelte';
	let hidden2 = true;
	let transitionParams = {
		x: -320,
		duration: 200,
		easing: sineIn
	};

	export let urlPath = '/';

	const drawers = [
		{
			name: 'Written',
			icon: 'fluent:note-edit-20-regular',
			path: '/admin/writtenview'
		},
		{
			name: 'Report',
			icon: 'octicon:report-24',
			path: '/admin/report'
		},
		{
			name: 'Withdraw',
			icon: 'uil:money-withdrawal',
			path: '/admin/withdraw'
		},
		{
			name: 'Writer',
			icon: 'fluent:notepad-person-24-regular',
			path: '/admin/writer'
		}
	];
</script>

<div class="text-center">
	<Button on:click={() => (hidden2 = false)}>
		<!-- Triple bar svg -->
		<div>
			<svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 60 60">
				<rect width="40" height="4" rx="2.5" ry="2.5" fill="#98A2B3" />
				<rect y="15" width="40" height="4" rx="2.5" ry="2.5" fill="#98A2B3" />
				<rect y="30" width="40" height="4" rx="2.5" ry="2.5" fill="#98A2B3" />
			</svg>
		</div>
	</Button>
</div>
<Drawer
	transitionType="fly"
	{transitionParams}
	bind:hidden={hidden2}
	id="sidebar2"
	class="bg-[#292932]"
>
	<div class="flex items-center">
		<h5 id="drawer-navigation-label-3" class="text-base font-semibold text-white uppercas">
			Manage
		</h5>
		<CloseButton on:click={() => (hidden2 = true)} class="mb-4 dark:text-white" />
	</div>
	<Sidebar>
		<SidebarWrapper divClass="overflow-y-auto py-4 px-3 rounded dark:bg-gray-800">
			<div class="py-4 overflow-y-auto">
				<ul class="space-y-2 font-medium">
					{#each drawers as drawer}
						<button
							on:click={() => {
								goto(drawer.path);
							}}
							class={`flex flex-col justify-center items-center transition duration-100 active:scale-95 ${
								urlPath == drawer.path ? 'text-[#F7B155]' : 'text-[#A1A1A1]'
							}`}
						>
							<div
								class="flex items-center p-2 text-white rounded-lg dark:text-white hover:bg-black dark:hover:bg-gray-700 group"
							>
								<Icon icon={drawer.icon} color="white" width="35" height="35" />
								<span class="ml-3">{drawer.name}</span>
							</div>
						</button>
					{/each}
				</ul>
			</div>
		</SidebarWrapper>
	</Sidebar>
</Drawer>
