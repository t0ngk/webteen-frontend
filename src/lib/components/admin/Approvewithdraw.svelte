<script>
  
	const data = [
	  {
		title: 'สวัสดีมะหมา',
		writer: 'Punim',
		amount: 100,
		
	  },
	  {
		title: 'สวัสดีมะหมี',
		writer: 'Punim1',
		amount: 200,
		
	  },
	  {
		title: 'สวัสดีครับเธอ',
		writer: 'Piunim3',
		amount: 300,
		
	  }
	];
  </script>
  
  <table class="w-full text-sm text-left text-white">
	<thead class="text-xs text-[#F7B155] uppercase border-t border-b border-gray-500 text-center">
		<tr>
		  <th scope="col" class="px-6 py-3"> Title </th>
		  <th scope="col" class="px-6 py-3"> Writer's name </th>
		  <th scope="col" class="px-6 py-3"> Amount </th>
		  <th scope="col" class="px-6 py-3"></th>
		</tr>
	  </thead>
	<tbody class="text-center">
	  {#each data as item (item.title)}
		<tr class="border-b border-gray-500">
		  <td class="px-6 py-4">{item.title}</td>
		  <td class="px-6 py-4">{item.writer}</td>
		  <td class="px-6 py-4">{item.amount}</td>
		  <td class="px-6 py-4">
			<div class="flex space-x-3">
				<button class="bg-[#F7B155] text-white px-2 py-[1.5px] rounded-full">Approve</button>
				<button class="bg-[#C13E3E] text-white px-2 py-[1.5px] rounded-full">Decline</button>
			</div>
		  </td>
		</tr>
	  {/each}
	</tbody>
  </table>
  