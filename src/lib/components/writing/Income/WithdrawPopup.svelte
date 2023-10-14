<script>
	import Icon from '@iconify/svelte';
	import { Button } from 'flowbite-svelte';

	export let isPopupOpen = false;
	export let title = '';
    export let coin = 0;

    let numberSelect = [100, 500, 1000]
    let customCoin = 0;
    let placeHolderCustomCoin = coin;
    let custom = false;
    let isChecked = false;
    let isChecked2 = false;

</script>

{#if isPopupOpen}
	<div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 bg-white rounded-lg w-[330px] h-auto p-8">
		<div class="text-black flex items-center">
			<h1 class="text-[22px] mb-2 font-bold flex-grow text-center">{title}</h1>
			<Button
				class="absolute right-0 top-5"
				on:click={() => {
					isPopupOpen = false;
				}}
			>
				<Icon
					icon="fluent-emoji-high-contrast:multiply"
					color="black"
					style="font-size: 16px"
					class=""
				/>
			</Button>
		</div>
        <div>
            <div class="flex items-center mt-2 px-3 hover:bg-gray-100 rounded-md">
                <input type="radio" id="fullAmount" name="radio" on:change={() => {custom = false; isChecked = true}}
                    class="w-4 h-4 focus:text-[#F7B155] focus:ring-0 focus:ring-offset-0">
                <label for="fullAmount" class="py-3 flex-grow ml-2 text-md font-semibold text-black">Full Amount</label>
                <label for="fullAmount" class="text-black font-semibold absolute right-12">{coin}</label>
            </div>
            <div class="flex items-center px-3 hover:bg-gray-100 rounded-md">
                <input type="radio" id="customlAmount" name="radio" checked={custom} on:change={() => {isChecked = true}}
                    class="w-4 h-4 focus:text-[#F7B155] focus:ring-0 focus:ring-offset-0">
                <label for="customlAmount" class="py-3 flex-grow ml-2 text-md font-semibold text-black">Custom Amount</label>
                <input type="number" min="0" max={coin} placeholder={placeHolderCustomCoin + ''} value={customCoin > 0 ? customCoin : ''}
                    class="font-semibold bg-gray-50 text-gray-900 text-md rounded-lg block w-14 p-2.5 [appearance:textfield] [&::-webkit-outer-spin-button]:appearance-none [&::-webkit-inner-spin-button]:appearance-none" required>
            </div>
            <div class="flex flex-row mt-2 mx-2 justify-between">
                {#each numberSelect as number}
                    <Button
                        class="w-[75px] h-7 border {coin >= number ? 'border-[#F7B155]' : 'border-[#D9D9D9]'}"
                        on:click={() => {
                            customCoin = number;
                            custom = true;
                            isChecked = true
                        }}
                        disabled={coin < number}
                    >
                        <p class="{coin >= number ? 'text-[#F7B155]' : 'text-[#D9D9D9]'} text-md font-semibold">{number}</p>
                    </Button>
                {/each}
            </div>
            <Button
                class="w-full h-9 mt-7 {isChecked && isChecked2 ? 'bg-[#F7B155]' : 'bg-[#D9D9D9]'}  rounded-xl"
                on:click={() => {
                    isPopupOpen = false;
                    isChecked = false;
                    isChecked2 = false;
                    custom = false;
                    customCoin = 0;
                }}
                disabled={!isChecked || !isChecked2}
            >
                <p class="text-[17px] font-bold text-black">CONFIRM</p>
            </Button>
            <div class="flex items-center mt-2 justify-center">
                <input id="checkbox" type="checkbox" class="w-3 h-3 text-blue-600 border-gray-300 rounded focus:ring-0 focus:ring-offset-0"
                    bind:checked={isChecked2}>
                <label for="checkbox" class="ml-2 text-[11px] font-semibold text-black">Wait for admin to approve for 2-3 days.</label>
            </div>
        </div>
	</div>
{/if}