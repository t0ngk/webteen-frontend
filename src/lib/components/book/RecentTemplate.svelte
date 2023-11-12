<script>
    import Icon from '@iconify/svelte';
    import { onMount } from 'svelte';
    import axios from 'axios';

    let recentRead = [];
    let historyBooks = [];
    let isDataLoad = false;
    let isDataLoaded = false;


    const getHistory = async () => {
		try {
			const res = await axios.get(
				`http://localhost:8082/history-service/getHistory`
			);
			historyBooks = res.data;
			isDataLoad = true; // Set the flag to true once data is loaded

            await getChapterHistory();
		} catch (error) {
			console.error('Error fetching books:', error);
		}
	};
    const getChapterHistory = async () => {
        try {
            const bookPromises = historyBooks.map(async (history) => {
                const chapterId = history.chapterId;
                const bookRes = await axios.get(`http://localhost:8082/history-service/getChapter/${chapterId}`);
                return bookRes.data;
            });

            const booksData = await Promise.all(bookPromises);
            console.log(">>>>>>>>>>>>>>> ", booksData)

            recentRead = booksData;
            isDataLoaded = true;
            console.log("(((((( ", recentRead);
        } catch (error) {
            console.error('Error fetching Books History:', error);
        }
    };
    onMount(getHistory);


</script>

<div class="mt-5">
    {#each recentRead as chapter}
        <div>
            <div class="bg-[#161218] flex border-b-[0.5px] border-gray-400 h-[85px]">
                <!-- <div class="w-[100px] bg-[#D9D9D9]"></div> -->
                <img src={chapter.cover} alt={chapter.title} class="w-[85px] h-[85px] object-cover" />
                <div class="flex justify-between items-center w-full pr-1">
                    <div class="items-center pl-5 justify-start">
                        <p class="text-base"><b>{chapter.title}</b></p>
                        <!-- <p class="text-base">Author</p> -->
                    </div>
                    <div class="justify-end">
                        <p class="text-base">#{chapter.number}</p>
                    </div>
                </div>
            </div>
        </div>
    {/each}
</div>