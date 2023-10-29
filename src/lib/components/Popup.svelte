<script>
	import Icon from '@iconify/svelte';
	import { Button } from 'flowbite-svelte';

	export let isPopupOpen = false;
	export let title = '';
</script>

{#if isPopupOpen}
	<div class="absolute top-20 left-9 bg-white rounded-[10px] w-[330px] h-auto p-8">
		<div class="text-black flex justify-between items-center">
			<h1 class="text-[20px] font-bold">{title}</h1>
			<Button
				class="w-8 p-2"
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
		<div class="text-black mt-5">
			<slot />
		</div>
	</div>
{/if}
