<script>
	import { Card, TabItem } from 'flowbite-svelte';
	import Icon from '@iconify/svelte';

	import PopupComment from '$lib/components/feed/PopupComment.svelte';
	import CommentFeed from '$lib/components/feed/Comment.svelte';

	let isCommentOpen = false;

	const feed = [
		{
			username: "Username",
			time: "12:00 PM",
			content: "Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.",
			profileImg: "https://media.discordapp.net/attachments/944667694517616720/1161428249423904939/download.jpg?ex=65384358&is=6525ce58&hm=7457ed7e5a96540c6140ccab11aa3da628c75058e89946f0a05c610e13e27335&=",
			img: "https://media.discordapp.net/attachments/944667694517616720/1162824440476872734/277813816_293521026266075_6147838200223765754_n.jpg?ex=653d57a6&is=652ae2a6&hm=44bc2d44b1c3247aa225180e85f965af17d1c4127550467cc1d85367a92a68ed&=&width=514&height=676",
			isLike: false,
			likeCount: 250,
			commentCount: 10,
		},
		{
			username: "Username2",
			time: "12:00 PM",
			content: "Say meow meow meow meow Oh girl you're the cat and lemme take you out Say meow meow meow meow we be like tom and jerrry lets go round and round (Woo)",
			profileImg: "https://media.discordapp.net/attachments/944667694517616720/1161428248958353478/292010181_2516048968532286_6221217547684299223_n.jpg?ex=65384358&is=6525ce58&hm=b761141208750b082615ed0a0b419c2804cf02c0142e96567d8b2a0fa8374a75&",
			img: "",
			isLike: true,
			likeCount: 1,
			commentCount: 1,
		},
		{
			username: "Username3",
			time: "12:00 PM",
			content: "Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.",
			profileImg: "https://media.discordapp.net/attachments/944667694517616720/1161428249197420584/279864473_1162633820977379_7150894201193670431_n.jpg?ex=65384358&is=6525ce58&hm=209dd2af238032a4299f7a3bf3a7c7e1c4d9ab2d2f5a1eafeddc516cbf1b0203&=",
			img: "https://media.discordapp.net/attachments/317865493090533376/1015721351748788384/unknown.png",
			isLike: false,
			likeCount: 0,
			commentCount: 0,
		},
	]

  </script>

<div class="h-full w-full p-2">
	<div class="flex justify-center text-center my-6 font-bold" >
		<a href="/feed" class=" bg-[#F7B155] text-black w-24 rounded-full mx-1">
			For You
		</a>
		<a href="/feed/following" class=" bg-trasparent text-white w-24 rounded-full mx-1">
			Following
		</a>
	</div>

	{#each feed as post}
		<Card class="m-5 p-5 rounded-xl bg-[#373739] border-transparent">
			<div class="flex my-2">
				<img class="w-10 h-10 rounded-full mr-3 object-cover"
				src={post.profileImg} alt="">
				<p class="my-2 text-xl font-bold tracking-tight text-gray-900 dark:text-white">
					{post.username}
				</p>
				<div class="ml-auto text-sm mt-4 text-md text-white">
					{post.time}
				</div>
			</div> 

			<p class="font-normal text-white leading-tight my-3">
				{post.content}
			</p>
			{#if post.img != ""}
				<img class="rounded-xl my-2 object-cover "
				src={post.img} alt=""
				/>
			{/if}

			<div class="flex text-white text-sm mt-2">
				<button
				on:click={() => { 
					post.isLike = !post.isLike;
				}}>
					<Icon icon={post.isLike === true ? "mdi:heart" : "clarity:heart-line"} color={post.isLike === true ? "#f7b155" : "white"} width="30px" />
				</button>
				<p class="mx-2 mt-2 font-semibold tracking">
					{post.likeCount > 1 ? post.likeCount + " likes" : post.likeCount + " like"}
				</p>

				<!-- comment -->
				<button
				on:click={() => { 
					isCommentOpen = !isCommentOpen; 
					// console.log('isCommentOpen : ' , isCommentOpen)
				}}>
					<Icon icon="iconamoon:comment-light" hFlip={true} width="30px"/>
				</button>
				<p class="mx-2 mt-2 font-semibold tracking">
					{post.commentCount > 1 ? post.commentCount + " comments" : post.commentCount + " comment"}
				</p>
			</div>
		</Card>
	{/each}

</div>

<!-- Popup -->
<PopupComment bind:isCommentOpen title={'Comments'}>
	<!-- <CommentFeed/> -->
</PopupComment>

