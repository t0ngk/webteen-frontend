<script>
	import { Card } from 'flowbite-svelte';
  </script>

<div class="h-full w-full p-2">
	<div class="flex justify-center text-center my-6 font-bold">
		<a href="/feed" class=" bg-[#F7B155] text-black w-24 rounded-full mx-1">
			For You
		</a>
		<a href="/feed/following" class=" bg-trasparent text-white w-24 rounded-full mx-1">
			Following
		</a>
	</div>

	<Card class="m-5 p-5 rounded-xl bg-[#373739] border-transparent">
		<div class="flex my-2">
			<img class="w-10 h-10 rounded-full mr-3"
			src="https://media.discordapp.net/attachments/944667694517616720/1161428249423904939/download.jpg?ex=65384358&is=6525ce58&hm=7457ed7e5a96540c6140ccab11aa3da628c75058e89946f0a05c610e13e27335&=" 
			alt="doraemon">
			<p class="my-2 text-xl font-bold tracking-tight text-gray-900 dark:text-white">
				Username
			</p>
			<div class="ml-auto text-sm mt-4 text-md text-white">
				12:00 PM
			</div>
		</div> 

		<p class="font-normal text-white leading-tight my-3">
			Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.
		</p>

		<img src="https://cdn.discordapp.com/attachments/317865493090533376/1015721353820782602/unknown.png"
		class="rounded-xl my-2" alt=""
		/>

		<div class="flex text-white text-sm mt-2">
			<svg xmlns="http://www.w3.org/2000/svg" width="32px" height="32px" viewBox="0 0 24 24" fill="white" stroke-opacity="0">
				<path fill-rule="evenodd" clip-rule="evenodd" d="M12 6.00019C10.2006 3.90317 7.19377 3.2551 4.93923 5.17534C2.68468 7.09558 2.36727 10.3061 4.13778 12.5772C5.60984 14.4654 10.0648 18.4479 11.5249 19.7369C11.6882 19.8811 11.7699 19.9532 11.8652 19.9815C11.9483 20.0062 12.0393 20.0062 12.1225 19.9815C12.2178 19.9532 12.2994 19.8811 12.4628 19.7369C13.9229 18.4479 18.3778 14.4654 19.8499 12.5772C21.6204 10.3061 21.3417 7.07538 19.0484 5.17534C16.7551 3.2753 13.7994 3.90317 12 6.00019Z" stroke="#000000" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
			</svg>
			<p class="mx-2 mt-2 font-semibold tracking">
				299 likes
			</p>
			<svg xmlns="http://www.w3.org/2000/svg" width="30px" height="30px" viewBox="0 0 24 24" id="Layer_1" data-name="Layer 1"><defs><style>.cls-1{fill:none;stroke:#020202;stroke-miterlimit:10;stroke-width:1.9px;}</style></defs><path class="cls-1" d="M21.5,12A9.5,9.5,0,1,0,12,21.5h9.5l-2.66-2.92A9.43,9.43,0,0,0,21.5,12Z"/></svg>
			<p class="mx-2 mt-2 font-semibold tracking">
				20 comments
			</p>
		</div>
	</Card>


</div>
