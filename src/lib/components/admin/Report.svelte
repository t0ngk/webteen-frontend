<script>
	const reportdata = [
		{
			image:
				'https://img.lovepik.com/free-png/20211201/lovepik-basketball-png-image_401244406_wh1200.png', // เพิ่ม path ของรูปภาพที่นี้
			username: 'PunimEIEI',
			Text: 'Proident sunt aliquip deserunt quis elit ex.',
			date: '3 June 2024'
		},
		{
			image: 'https://i.pinimg.com/736x/fc/40/a8/fc40a8296427427a88b4bc682f6f7325.jpg', // เพิ่ม path ของรูปภาพที่นี้
			username: 'PunimKIKI',
			Text: 'Aliquip non pariatur qui et adipisicing consectetur incididunt minim anim.',
			date: '4 June 2024'
		},
		{
			image: 'https://cisalvvf.org/wp-content/uploads/2022/11/dog.jpg', // เพิ่ม path ของรูปภาพที่นี้
			username: 'PunimJIJI',
			Text: 'Incididunt in aliquip duis aliqua ea veniam mollit eiusmod officia mollit et nostrud.',
			date: '5 June 2024'
		},
		{
			image: 'https://cisalvvf.org/wp-content/uploads/2022/11/dog.jpg', // เพิ่ม path ของรูปภาพที่นี้
			username: 'PunimJIJI',
			Text: 'Incididunt in aliquip duis aliqua ea veniam mollit eiusmod officia mollit et nostrud.',
			date: '6 June 2024'
		}
        
	];
</script>

{#each reportdata as item (item.username)}
	<div class="p-4 my-4 border-b border-gray-500 flex space-x-6 relative">
		<div class="w-12 h-12 rounded-full overflow-hidden">
			<img src={item.image} alt={item.image} class="object-cover w-full h-full" />
		</div>
		<div class="flex-1">
			<div class="flex items-center justify-between">
				<p class="font-bold text-xl mb-5">{item.username}</p>
				<div class="flex space-x-2 mt-[-20px]">
					<button class="bg-[#C13E3E] text-white px-2 py-[1.5px] rounded-full">Delete</button>
					<button class="bg-[#929292] text-white px-2 py-[1.5px] rounded-full">Decline</button>
				</div>
			</div>
			<p class="text-gray-400 mb-5">{item.Text}</p>
			<p class="text-gray-400">{item.date}</p>
		</div>
	</div>
{/each}
