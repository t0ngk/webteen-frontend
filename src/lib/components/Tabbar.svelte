<script>
	import { goto } from '$app/navigation';
	import Icon from '@iconify/svelte';
  import editIcon from '@iconify/icons-material-symbols/edit';
  import homeIcon from '@iconify/icons-material-symbols/home-rounded';
  import categoryIcon from '@iconify/icons-material-symbols/category-rounded';
  import feedIcon from '@iconify/icons-material-symbols/feed-rounded';
  import personIcon from '@iconify/icons-material-symbols/person-rounded';

  export let urlPath = '/';

	const tabs = [
		{
			name: 'Home',
			icon: homeIcon,
			path: '/'
		},
		{
			name: 'Category',
			icon: categoryIcon,
			path: '/category'
		},
		{
			name: 'Writing',
			icon: editIcon,
			path: '/writing'
		},
		{
			name: 'Profile',
			icon: personIcon,
			path: '/profile'
		}
	];
</script>

<div class="px-4 py-2 w-full flex justify-between select-none">
	{#each tabs as tab}
		<button
			on:click={() => {
				goto(tab.path);
			}}
			class={`flex flex-col justify-center items-center transition duration-100 active:scale-95 ${
				urlPath == tab.path ? 'text-[#F7B155]' : 'text-[#A1A1A1]'
			}`}
		>
			<Icon class="w-auto h-7" icon={tab.icon} />
			<p class="text-xs">{tab.name}</p>
		</button>
	{/each}
</div>
