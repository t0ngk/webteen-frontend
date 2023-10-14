<script>
    let yes = false;
</script>

<div class="flex justify-center text-center items-center h-[95%] p-2">
    <form class="flex flex-col space-y-5 w-10/12" action="/">
        <h1 class="flex text-2xl mt-6 text-white font-bold">Log in</h1>
        
        <input class="shadow appearance-none border bg-transparent border-[#B4B4B4] rounded-3xl w-full p-3 text-[#B4B4B4] text-xs font-semibold leading-tight focus:outline-none focus:shadow-outline"
        name="email" 
        placeholder="Email / Username" 
        required
        type="email"
        
        />
        <input class="shadow appearance-none border bg-transparent border-[#B4B4B4] rounded-3xl w-full p-3 text-[#B4B4B4] text-xs font-semibold leading-tight focus:outline-none focus:shadow-outline"
        name="password"
        placeholder="Password"
        type="password"
        required
        />

        <div class="flex font-medium text-sm px-2">
            <input class="mr-2  bg-transparent checked:bg-yellow-500" 
                type="checkbox" bind:checked={yes} />
            <p class="">
                Remember me
            </p>
            <a href="/login" class="ml-auto text-[#F7B155] hover:underline dark:text-yellow-600"
            on:click={() => console.log("forgotpassword")}
            >
                Forgot password ?
            </a>
        </div>

        <div></div>
        <button class=" text-black bg-[#F7B155] h-10 rounded-3xl font-bold text-sm tracking-wide disabled:bg-[#838383]"
        disabled={!yes} on:click={() => console.log("login")}>
            LOGIN
        </button>

    </form>
</div>
<div class="text-center text-white font-medium text-sm mb-5">
    <p>
        Don't have an account ? 
        <a href="/signup" class="ml-1 text-[#F7B155] hover:underline dark:text-yellow-600">Sign up</a>
    </p>
</div>