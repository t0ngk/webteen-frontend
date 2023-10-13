<script>
	import { goto } from '$app/navigation';

	const writen = [
		{
			image:
				'https://img.lovepik.com/free-png/20211201/lovepik-basketball-png-image_401244406_wh1200.png', // เพิ่ม path ของรูปภาพที่นี้
			username: 'PunimEIEI',
			date: '3 June 2024',
			status: 'Waiting'
		},
		{
			image: 'https://i.pinimg.com/736x/fc/40/a8/fc40a8296427427a88b4bc682f6f7325.jpg', // เพิ่ม path ของรูปภาพที่นี้
			username: 'PunimKIKI',
			date: '4 June 2024',
			status: 'Waiting'
		},
		{
			image: 'https://cisalvvf.org/wp-content/uploads/2022/11/dog.jpg', // เพิ่ม path ของรูปภาพที่นี้
			username: 'PunimJIJI',
			date: '5 June 2024',
			status: 'Waiting'
		}
	];
</script>

<table class="w-full text-sm text-left text-white border-collapse border-t border-gray-500">
	<thead class="text-xs text-[#F7B155] uppercase border-b text-center border-gray-500">
		<tr>
			<th scope="col" class="px-8 py-3 text-left"> User </th>
			<th scope="col" class="px-6 py-3"> Date </th>
			<th scope="col" class="px-6 py-3"> Status </th>
			<th scope="col" class="px-6 py-3" />
		</tr>
	</thead>
	<tbody class="text-center">
		{#each writen as item (item.username)}
			<tr class="border-gray-500">
				<td class="px-6 py-4">
					<div class="flex items-center">
						<div class="w-12 h-12 rounded-full overflow-hidden">
							<img src={item.image} alt={item.image} class="object-cover w-full h-full" />
						</div>
						<div class="ml-4">
							{item.username}
						</div>
					</div>
				</td>
				<td class="px-6 py-4">{item.date}</td>
				<td class="flex items-center justify-center mt-6">
					{#if item.status === 'Approved'}
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
				<td>
					<button
						on:click={() => {
							goto('/admin/writerdetail');
						}}
					>
						<p class="hover:text-[#F7B155]">View</p>
					</button>
				</td>
			</tr>
		{/each}
	</tbody>
</table>
