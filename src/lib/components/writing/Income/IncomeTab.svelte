<script>
	import IncomeHistory from "./IncomeHistory.svelte";
	import WithdrawHistory from "./WithdrawHistory.svelte";

    const tabs = [
		{
			name: 'Income',
            component: IncomeHistory
		},
        {
			name: 'Withdraw',
            component: WithdrawHistory
		},
	];

    let activeTab = tabs[0]

</script>

<div class="flex flex-row h-9 mx-6 my-5 rounded-lg bg-[#373739]">
    {#each tabs as tab}
        <button
            on:click={() => {
                activeTab = tab
            }}
            class="w-1/2 rounded-lg flex items-center justify-center {activeTab.name === tab.name ? 'border-2 border-[#F7B155]' : ''}"
        >
            <p class="text-md {activeTab.name === tab.name ? 'text-[#F7B155]' : 'text-[#F1F2F450]'} ">{tab.name}</p>
        </button>
    {/each}
</div>

<svelte:component this={activeTab.component} />