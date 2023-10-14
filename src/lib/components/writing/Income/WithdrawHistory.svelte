<script>
    import Icon from '@iconify/svelte';

    const withdrawHistory = [
        {
            name: 'No Name 404',
            date: '10/09/2023',
            time: '19:04',
            coin: 15,
            status: false,
        },
        {
            name: 'อ่านฉันสิ',
            date: '09/12/2020',
            time: '07:00',
            coin: 5,
            status: false,
        },
        {
            name: 'กระต่ายกับเต่า',
            date: '12/03/2016',
            time: '23:23',
            coin: 100,
            status: false,
        },
        {
            name: 'No Name 404',
            date: '10/09/2023',
            time: '19:04',
            coin: 15,
            status: false,
        },
        {
            name: 'อ่านฉันสิ',
            date: '09/12/2020',
            time: '07:00',
            coin: 5,
            status: false,
        },
        {
            name: 'กระต่ายกับเต่า',
            date: '12/03/2016',
            time: '23:23',
            coin: 100,
            status: true,
        },
        {
            name: 'No Name 404',
            date: '10/09/2023',
            time: '19:04',
            coin: 15,
            status: true,
        },
        {
            name: 'อ่านฉันสิ',
            date: '09/12/2020',
            time: '07:00',
            coin: 5,
            status: true,
        },
        {
            name: 'กระต่ายกับเต่า',
            date: '12/03/2016',
            time: '23:23',
            coin: 100,
            status: true,
        },
        {
            name: 'No Name 404',
            date: '10/09/2023',
            time: '19:04',
            coin: 15,
            status: true,
        },
        {
            name: 'อ่านฉันสิ',
            date: '09/12/2020',
            time: '07:00',
            coin: 5,
            status: true,
        },
        {
            name: 'กระต่ายกับเต่า',
            date: '12/03/2016',
            time: '23:23',
            coin: 100,
            status: true,
        },
    ]
</script>

{#each withdrawHistory as history}
    <div class="flex flex-row border-b border-[#FFFFFF50] h-16 mx-8 items-center justify-between">
        <div>
            <p class="text-white text-md pb-1">{history.name}</p>
            <p class="text-[#818181] text-xs">{history.date} | {history.time}</p>
        </div>
        <div class="flex flex-row items-center">
            <div class="flex items-center w-[70px]">
                <Icon icon="solar:dollar-minimalistic-bold" color="#f7b155" class="text-lg" />
                <p class="text-lg font-semibold text-[#F7B155] ml-1">-</p>
                <p class="text-lg font-semibold text-[#F7B155]">{history.coin}</p>
            </div>
            <div class="flex py-1 w-20 rounded-full {history.status === false ? 'bg-[#D9D9D980]' : 'border border-[#F7B155]' }  justify-center">
                <p class="{history.status === false ? 'text-[#161218] font-semibold' : 'text-[#F7B155]'} text-xs ">{history.status === false ? 'Waiting' : 'Success'}</p>
            </div>
        </div>
    </div>
{/each}