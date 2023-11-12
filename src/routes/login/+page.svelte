<script>
    let username = null;
    let password = null;
</script>

<div class="flex justify-center text-center items-center h-[95%] p-2">
    <div class="flex flex-col space-y-5 w-10/12">
        <h1 class="flex text-2xl mt-6 text-white font-bold">Log in</h1>
        
        <input class="shadow appearance-none border bg-transparent border-[#B4B4B4] rounded-3xl w-full p-3 text-[#B4B4B4] text-xs font-semibold leading-tight focus:outline-none focus:shadow-outline"
        name="email"
        placeholder="Username"
        required
        bind:value={username}
        />
        <input class="shadow appearance-none border bg-transparent border-[#B4B4B4] rounded-3xl w-full p-3 text-[#B4B4B4] text-xs font-semibold leading-tight focus:outline-none focus:shadow-outline"
        name="password"
        placeholder="Password"
        type="password"
        required
        bind:value={password}
        />

        <!-- <div class="flex font-medium text-sm px-2">
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
        </div> -->

        <div></div>
        <button class=" text-black bg-[#F7B155] h-10 rounded-3xl font-bold text-sm tracking-wide disabled:bg-[#838383]"
        on:click={async () => {
            const req = await fetch('http://localhost:8082/auth-service/login', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    username: username,
                    password: password
                })
            });
            if (req.ok) {
                const {accessToken, refreshToken, isError, message} = await req.json();
                if (isError) {
                    alert(message);
                } else {
                    localStorage.setItem('accessToken', accessToken);
                    localStorage.setItem('refreshToken', refreshToken);
                    window.location.href = '/';
                }
            } else {
                alert('Login failed');
            }
        }}>
            LOGIN
        </button>

    </div>
</div>
<div class="text-center text-white font-medium text-sm mb-5">
    <p>
        Don't have an account ? 
        <a href="/signup" class="ml-1 text-[#F7B155] hover:underline dark:text-yellow-600">Sign up</a>
    </p>
</div>
