<script>
	export let selectedStatus = ""; // รับค่า selectedStatus ผ่าน props
	import { goto } from '$app/navigation';

	const data = [
		{
			title: 'สวัสดีมะหมา',
			writer: 'Punim1',
			amount: 100,
			status: 'Approve'
		},
		{
			title: 'สวัสดีมะหมี',
			writer: 'Punim2',
			amount: 100,
			status: 'Decline'
		},
		{
			title: 'สวัสดีครับเธอ',
			writer: 'Punim3',
			amount: 100,
			status: 'Waiting'
		},
		{
			title: 'ไง',
			writer: 'Punim3',
			amount: 100,
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
			<th scope="col" class="px-6 py-3 w-[100px]"> Status </th>
			<th scope="col" class="px-6 py-3" />
		</tr>
	</thead>
	<tbody class="text-center">
		{#each data as item (item.title)}
		{#if selectedStatus === '' || item.status === selectedStatus}
				<tr class="border-b border-gray-500">
					<td class="px-6 py-4">{item.title}</td>
					<td class="px-6 py-4">{item.writer}</td>
					<td class="px-6 py-4">{item.amount}</td>
					<td class="px-6 py-4">
						{#if item.status === 'Approve'}
							<div
								class="w-[80px] h-[25px] bg-[#38920D] rounded-full text-white font-semibold flex items-center justify-center"
							>
								{item.status}
							</div>
						{:else if item.status === 'Decline'}
							<div
								class="w-[80px] h-[25px] bg-[#C13E3E] rounded-full text-white font-semibold flex items-center justify-center"
							>
								{item.status}
							</div>
						{:else if item.status === 'Waiting'}
							<div
								class="w-[80px] h-[25px] bg-[#929292] rounded-full text-white font-semibold flex items-center justify-center"
							>
								{item.status}
							</div>
						{/if}
					</td>
					<td class="px-6 py-4">
						<button
							on:click={() => {
								goto('/admin/approvewithdraw');
							}}
						>
							<p class="hover:text-[#F7B155]">View</p>
						</button>
					</td>
				</tr>
			{/if}
		{/each}
	</tbody>
</table>
