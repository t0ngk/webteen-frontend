<script>
	const data = [
		{
			title: 'Book Title 1',
			writer: 'Author 1',
			amount: 100,
			status: 'Approved'
		},
		{
			title: 'Book Title 2',
			writer: 'Author 2',
			amount: 200,
			status: 'Decline'
		},
		{
			title: 'Book Title 3',
			writer: 'Author 3',
			amount: 300,
			status: 'Waiting'
		}
	];
</script>

<table class="w-full text-sm text-left text-white">
	<thead class="text-xs text-[#F7B155] uppercase border-t border-b border-gray-500 text-center">
		<tr>
			<th scope="col" class="px-6 py-3"> Title </th>
			<th scope="col" class="px-6 py-3"> Writer's name </th>
			<th scope="col" class="px-6 py-3"> Amount </th>
			<th scope="col" class="px-6 py-3"> Status </th>
		</tr>
	</thead>
	<tbody class="text-center">
		{#each data as item (item.title)}
			<tr class="border-b border-gray-500">
				<td class="px-6 py-4">{item.title}</td>
				<td class="px-6 py-4">{item.writer}</td>
				<td class="px-6 py-4">{item.amount}</td>
				<td class="flex items-center justify-center mt-3">
					{#if item.status === 'Approved'}
						<div class="w-[80px] h-[25px] bg-[#38920D] rounded-full text-white font-semibold flex items-center justify-center">
							{item.status}
						</div>
					{:else if item.status === 'Decline'}
						<div class="w-[80px] h-[25px] bg-[#C13E3E] rounded-full text-white font-semibold flex items-center justify-center">
							{item.status}
						</div>
					{:else if item.status === 'Waiting'}
						<div class="w-[80px] h-[25px] bg-[#929292] rounded-full text-white font-semibold flex items-center justify-center">
							{item.status}
						</div>
					{/if}
				</td>
			</tr>
		{/each}
	</tbody>
</table>
