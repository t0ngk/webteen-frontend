<script>
	import Icon from "@iconify/svelte";

    const coinHistory = [
		{
			coinNumber: '9,999',
			date: '19/9/2023',
            time: '12.00 pm'
		},
		{
			coinNumber: '9,999',
			date: '19/9/2023',
            time: '12.00 pm'
		},
		{
			coinNumber: '9,999',
			date: '19/9/2023',
            time: '12.00 pm'
		},
		{
			coinNumber: '9,999',
			date: '19/9/2023',
            time: '12.00 pm'
		},
		{
			coinNumber: '9,999',
			date: '19/9/2023',
            time: '12.00 pm'
		},
	];
</script>

<div class="h-full w-full p-2 pt-5">
    {#each coinHistory as item}
        <div class="flex border-b-[1px] border-[#373739] py-3 items-center">
            <div>
                <Icon icon="circum:bitcoin" color="#f7b155" class="h-[30px] w-[30px]" />
            </div>
            <div class="pl-3">
                <p class="mb-1"><b>{item.coinNumber}</b></p>
                <div class="flex items-center">
                    <p class="text-xs">{item.date}</p>
                    <p class="pl-2 text-xs">{item.time}</p>
                </div>
            </div>
        </div>
    {/each}
</div>