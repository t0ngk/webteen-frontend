<script>
	import { Button } from "flowbite-svelte";
    import BookOwned from "../book/BookOwned.svelte";

</script>


<div class="h-full w-full p-[1px] mt-5">
    <div class="flex justify-between">
        <div class="pl-2">
            <p><b>My Post</b></p>
        </div>
        <Button class="border-[2px] border-white bg-[#D9D9D9] px-3">
            <p class="text-slate-950"><b>view all</b></p>
        </Button>
    </div>
    <div class="grid grid-cols-3 gap-3 my-3">
        <BookOwned/>
    </div>
</div>