<script>
	import { Button } from "flowbite-svelte";
    import BookOwned from "../book/BookOwned.svelte";
    import Icon from '@iconify/svelte';

</script>


<div class="h-full w-full p-[1px] mt-5">
    <div class="pl-2">
        <p><b>My Written</b></p>
    </div>
    <div class="my-3">
        <div class="bg-[#373739] rounded-xl p-5">
            <p class="text-xs mb-3 text-right">12.00 PM, 21 Nov 2020</p>
            <div class="flex flex-row items-center">
                <div class="h-[32px] w-[32px] rounded-full border-solid border-[2px] border-amber-300"></div>
                <p class="text-sm pl-2"><b>Sweet And Soupy</b></p>
            </div>
            <div class="bg-slate-300 w-full h-36 mt-4"></div>
            <p class="text-sm mt-4">Lorem ipsum, dolor sit amet consectetur 
                adipisicing elit. Voluptates consequatur veritatis ducimus, 
                pariatur deserunt, voluptatum unde illo voluptate
            </p>
            <div class="flex">
                <div class="flex items-center mt-3">
                    <Icon icon="ph:heart-fill" color="#FA5252" class="w-[15px] h-[15px]" />
                    <p class="text-xs pl-1">20</p>
                </div>
                <div class="flex items-center mt-3 pl-3">
                    <Icon icon="bi:chat-fill" color="white" class="w-[15px] h-[15px]" />
                    <p class="text-xs pl-1">10</p>
                </div>
            </div>
        </div>
    </div>

    <div class="my-3">
        <div class="bg-[#373739] rounded-xl p-5">
            <p class="text-xs mb-3 text-right">12.00 PM, 21 Nov 2020</p>
            <div class="flex flex-row items-center">
                <div class="h-[32px] w-[32px] rounded-full border-solid border-[2px] border-amber-300"></div>
                <p class="text-sm pl-2"><b>Sweet And Soupy</b></p>
            </div>
            <p class="text-sm mt-4">Lorem ipsum, dolor sit amet consectetur 
                adipisicing elit. Voluptates consequatur veritatis ducimus, 
                pariatur deserunt, voluptatum unde illo voluptate
            </p>
            <div class="flex">
                <div class="flex items-center mt-3">
                    <Icon icon="ph:heart-fill" color="#FA5252" class="w-[15px] h-[15px]" />
                    <p class="text-xs pl-1">20</p>
                </div>
                <div class="flex items-center mt-3 pl-3">
                    <Icon icon="bi:chat-fill" color="white" class="w-[15px] h-[15px]" />
                    <p class="text-xs pl-1">10</p>
                </div>
            </div>
        </div>
    </div>
</div>