<script>
	import Icon from '@iconify/svelte';
	import { Button } from 'flowbite-svelte';

	export let isCommentOpen = false;
	export let title = '';

    const comments = [
        {
            username: "Fluk",
            profileImg: "https://media.discordapp.net/attachments/944667694517616720/1161428249197420584/279864473_1162633820977379_7150894201193670431_n.jpg?ex=65384358&is=6525ce58&hm=209dd2af238032a4299f7a3bf3a7c7e1c4d9ab2d2f5a1eafeddc516cbf1b0203&=",
            time: "4h",
            content: "Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.",
            isLike: false,
            likeCount: 10,
            commentCount: 2,
        },
        {
            username: "Pear",
            profileImg: "https://media.discordapp.net/attachments/944667694517616720/1162824439692525738/277587276_2132556140253063_1961910096568618274_n.jpg?ex=653d57a6&is=652ae2a6&hm=009f4e061f348e7ac374ac89780c6eedef2c4a1f0129281b40693b5c292841eb&=",
            time: "1w",
            content: "Here are the biggest ",
            isLike: true,
            likeCount: 10,
            commentCount: 2,
        },
        {
            username: "User",
            profileImg: "https://media.discordapp.net/attachments/944667694517616720/1162824440476872734/277813816_293521026266075_6147838200223765754_n.jpg?ex=653d57a6&is=652ae2a6&hm=44bc2d44b1c3247aa225180e85f965af17d1c4127550467cc1d85367a92a68ed&=&width=514&height=676",
            time: "2 days ago kids",
            content: "awesome !",
            isLike: true,
            likeCount: 1,
            commentCount: 1,
        },
        {
            username: "to everyone",
            profileImg: "https://media.discordapp.net/attachments/944667694517616720/1162824440074223738/279010305_2453388174798366_937123755452021445_n.jpg?ex=653d57a6&is=652ae2a6&hm=91dab1d5d9752f0b49f782b3a33d2d697ec4e4a57b63119f33dd7b3c50aad07f&=&width=540&height=676",
            time: "1s",
            content: "เลื่อนลงไม่ได้จ้า",
            isLike: false,
            likeCount: 0,
            commentCount: 0,
        },
        // {
        //     username: "User",
        //     profileImg: "https://media.discordapp.net/attachments/944667694517616720/1162824440074223738/279010305_2453388174798366_937123755452021445_n.jpg?ex=653d57a6&is=652ae2a6&hm=91dab1d5d9752f0b49f782b3a33d2d697ec4e4a57b63119f33dd7b3c50aad07f&=&width=540&height=676",
        //     time: "1s",
        //     content: "what ru doing ?",
        //     isLike: false,
        //     likeCount: 0,
        //     commentCount: 0,
        // },
    ]
    
</script>

{#if isCommentOpen}
	<div class="absolute bottom-0 bg-black rounded-t-[30px] w-full h-[65%]">
		<div class="text-white text-center">
			<h1 class="text-[20px] font-bold mt-6 text-[#F7B155] ">{title}</h1>
            <Button
				class="w-8 p-2"
				on:click={() => {
					isCommentOpen = false;
				}}
			>
				<Icon
					icon="fluent-emoji-high-contrast:multiply"
					color="white"
					style="font-size: 16px"
					class=""
				/>
			</Button>
            <hr class="mt-4 h-px border-0 dark:bg-[#83838390]">

            <!-- Comment -->
            {#each comments as comment}
                <div class="flex flex-row mt-3">

                    <div class="mr-4 pt-2 justify-center">
                        <img class="w-10 h-10 rounded-full object-cover mx-5"
                                src={comment.profileImg} alt="">
                    </div>

                    <div class="mr-2 w-11/12 text-white ">
                        <div class="flex">
                            <p class="mt-2 mb-1 text-md font-bold tracking-tight">
                                {comment.username}
                            </p>
                            <div class="ml-2 text-xs mt-3.5 text-[#B8B8B8]">
                                {comment.time}
                            </div>
                        </div>
                        <p class="font-normal text-sm leading-5 text-start">
                            {comment.content}
                        </p>
                        <div class="flex text-white text-xs mt-2">
                            
                            <button on:click={() => { 
                                comment.isLike = !comment.isLike;
                            }}>
                                <Icon icon={comment.isLike === true ? "mdi:heart" : "clarity:heart-line"} color={comment.isLike === true ? "#f7b155" : "white"} width="20px" />
                            </button>
                            <p class="mx-2 mr-3 mt-1 font-semibold tracking">
                                {comment.likeCount}
                            </p>
                            
                            <Icon icon="iconamoon:comment-light" hFlip={true} width="20px" />
                            <p class="mx-2 mt-1 font-semibold tracking">
                                {comment.commentCount}
                            </p>
                        </div>
                    </div> 

                    <div class="mr-7 pt-5 items-center justify-start flex flex-col flex-grown ">
                        <Icon icon="bi:three-dots" class="mb-5" color="#b8b8b8" rotate={1} />
                    </div>

                </div>
            {/each}

            <!-- write comment -->
            <div class="flex pt-2 my-4 bottom-0 absolute w-full bg-black">
                <img class="w-10 h-10 rounded-full object-cover mx-5"
                        src="https://media.discordapp.net/attachments/944667694517616720/1162824439692525738/277587276_2132556140253063_1961910096568618274_n.jpg?ex=653d57a6&is=652ae2a6&hm=009f4e061f348e7ac374ac89780c6eedef2c4a1f0129281b40693b5c292841eb&=" alt="">
                <input class="shadow appearance-none border bg-white border-[#B4B4B4] rounded-3xl w-8/12 p-3 text-black text-xs font-semibold leading-tight focus:outline-none focus:shadow-outline"
                name="writeComment" 
                placeholder="Write comment" 
                type="text"
                />
                <Icon icon="fluent:send-16-regular" class="mx-2 flex flex-grow " width="33px" />

            </div>

            

            

		</div>
	</div>
{/if}
