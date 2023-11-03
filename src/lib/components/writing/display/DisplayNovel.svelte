<script>
	import Icon from '@iconify/svelte';
	import { goto } from '$app/navigation';

	let text = `Test`;
	let isBold = false;
	let isItalic = false;
	let isUnderline = false;
	let isLeft = false;
	let isCenter = false;
	let isRight = false;

	function toggleBold() {
		isBold = !isBold;
	}

	function toggleItalic() {
		isItalic = !isItalic;
	}

	function toggleUnderline() {
		isUnderline = !isUnderline;
	}

	function toggleLeft() {
		isLeft = true;
		isCenter = false;
		isRight = false;
	}

	function toggleCenter() {
		isCenter = true;
		isLeft = false;
		isRight = false;
	}

	function toggleRight() {
		isRight = true;
		isLeft = false;
		isCenter = false;
	}
</script>

<div class="mt-5">
	<div class="w-full h-10 items-center flex bg-[#ebebeb] border-b-[2px] border-[#6565693f]">
		<div class="border-r-[1px] border-[#56565a] flex items-center h-5">
			<button class="m-2" on:click={toggleBold}>
				<Icon icon="ooui:bold-b" style="font-size: 14px" class="text-black" />
			</button>
			<button class="mr-2" on:click={toggleItalic}>
				<Icon icon="fa-solid:italic" style="font-size: 14px" class="text-black" />
			</button>
			<button class="mr-2" on:click={toggleUnderline}>
				<Icon icon="gridicons:underline" style="font-size: 18px" class="text-black" />
			</button>
		</div>
		<div class="border-r-[1px] border-[#656569bd] flex items-center h-5">
			<button class="m-2" on:click={toggleLeft}>
				<Icon icon="icon-park:align-text-left" style="font-size: 18px" class="text-black" />
			</button>
			<button class="mr-2" on:click={toggleCenter}>
				<Icon icon="icon-park:align-text-center" style="font-size: 18px" class="text-black" />
			</button>
			<button class="mr-2" on:click={toggleRight}>
				<Icon icon="icon-park:align-text-right" style="font-size: 18px" class="text-black" />
			</button>
		</div>
	</div>
	<textarea
		class={`w-full h-[42rem] text-black p-2 ${isLeft && 'text-left'} ${isCenter && 'text-center'} ${
			isRight && 'text-right'
		} ${isBold && 'font-bold'} ${isItalic && 'italic'} ${isUnderline && 'underline'}`}
		bind:value={text}
	/>
</div>

<style>
</style>
