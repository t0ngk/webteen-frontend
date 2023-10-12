<script>
	import Search from '$lib/components/admin/Search.svelte';
	import Icon from '@iconify/svelte';
	import { goto } from '$app/navigation';

	const writtens = [
		{
			id_written: '01',
			name: 'Manga name',
			penname: 'Penname',
			image: '',
			time: '30/06/23',
			status: 'Waiting',
		},
	]
</script>

<div class="h-full w-full p-5">
	<Search />
	<h1 class="text-2xl">Written</h1>
	<p>More than 400+ new written</p>

	<div class="relative overflow-x-auto py-5">
		<table class="w-full text-sm text-left text-gray-500">
			<thead class="text-xs text-white uppercase bg-[#292932]">
				<tr>
					<th scope="col" class="px-6 py-3"> NAME </th>
					<th scope="col" class="px-6 py-3"> TIME </th>
					<th scope="col" class="px-6 py-3"> STATUS </th>
					<th scope="col" class="px-6 py-3"> </th>
				</tr>
			</thead>
			<tbody>
				<!--  -->
				{#each writtens as written }
				<tr class="border-b border-[#7C7C7C] text-white">
					<th scope="row" class="px-6 py-4 font-medium whitespace-nowrap">
							<div class="flex flex-row">
							<img
								src="{written.image}"
								class=" h-12 w-12 max-w-sm rounded-lg shadow-none transition-shadow duration-300 ease-in-out hover:shadow-lg hover:shadow-black/30"
								alt=""
							/>
							<div class="px-3">
								<p class="px-1 text-[#BABABA]">{written.name}</p>
								<div class="flex flex-row">
									<Icon class="p-1" icon="solar:user-bold" color="#818181" width="22" height="21" />
									<p class="text-[#BABABA]">{written.penname}</p>
								</div>
							</div>
						</div>
					</th>
					<td class="px-6 py-4"> {written.time} </td>
					<td class="px-6 py-4 pt-7 flex flex-row">
						<div class="bg-[#F7B155] rounded-xl text-black p-1">
							<p>{written.status}</p>
						</div>
					</td>
					<td>
						<button on:click={() => {goto("/admin/writtenapprove");}}>
							<p class="hover:text-[#F7B155]">View</p>
						</button>
					</td>
				</tr>
				{/each}
			</tbody>
		</table>
	</div>
</div>
