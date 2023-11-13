<script>
	import Icon from '@iconify/svelte';
	import { onMount } from 'svelte';
	import axios from 'axios';

	let FavoriteBooks = [];
	let Books = [];
	let isDataLoad = false;
	let isDataLoaded = false;

	const getFavorite = async () => {
		try {
			const res = await axios.get('http://localhost:8082/favorite-service/getFavorite');
			FavoriteBooks = res.data;
			isDataLoaded = true; // Set the flag to true once data is loaded
			console.log(FavoriteBooks);

			// เมื่อดึงข้อมูลจาก 'favorite-service' เสร็จสิ้น, ทำการดึงข้อมูล Books
			await getBooksFromFavorite();
		} catch (error) {
			console.error('Error fetching favorite:', error);
		}
	};

	const getBooksFromFavorite = async () => {
		try {
			// สร้าง Promise สำหรับทุกการดึงข้อมูล Books
			const bookPromises = FavoriteBooks.map(async (favorite) => {
				const bookId = favorite.bookId;
				const bookRes = await axios.get(`http://localhost:8082/favorite-service/getBook/${bookId}`);
				return bookRes.data;
			});

			// รอให้ทุก Promise เสร็จสิ้น
			const booksData = await Promise.all(bookPromises);

			// นำข้อมูล Books ทั้งหมดมาเก็บในตัวแปร Books
			Books = booksData;
			isDataLoad = true; // Set the flag to true once data is loaded
			console.log(Books);
		} catch (error) {
			console.error('Error fetching Books:', error);
		}
	};

    const deleteFavorite = async (bookId) => {
        const bookID = bookId
        console.log(`favId >>>>>> ${bookID}`);
		try {
			const deleteRes = await axios.get(`http://localhost:8082/favorite-service/deleteFavorite/${bookID}`);
			console.log(`Favorite with ID ${bookId} deleted`);
		} catch (error) {
			console.error('Error deleting favorite:', error);
		}
	};


	onMount(getFavorite);

	
</script>

<div class="mt-5">
	{#each Books as book}
		<div>
			<div class="bg-[#161218] flex border-b-[0.5px] border-gray-400 h-[85px]">
                <img src={book.cover} alt={book.title} class="w-[85px] h-[85px] object-cover" />
				<div class="flex justify-between items-center w-full pr-1">
					<div class="items-center pl-5 justify-start">
						<p class="text-base"><b>{book.title}</b></p>
						<p class="text-base">{book.like}</p>
					</div>
					<button class="justify-end" on:click={deleteFavorite(book.bookId)}>
						<Icon icon="ph:heart-fill" color="#F7B155" class="w-[25px] h-[25px]" />
					<button/>
				</div>
			</div>
		</div>
	{/each}
</div>
