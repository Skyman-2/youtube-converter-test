<script>
    let videos = [];
    let searchTerm = '';
    let searchValue = '';
    const APIKey = 'AIzaSyAIf3dNZ7Pk5ecv4FK6K48B2S1HoAYFHW8'
    
    async function handleNewSearch(searchTerm) {
        if (searchTerm == '') {
            return;
        }
        const url = `https://youtube.googleapis.com/youtube/v3/search?part=snippet&maxResults=25&q=${searchTerm}&key=${APIKey}`
        const res = await fetch(url);
        const data = await res.json();
        console.log(data.items);
        videos = data.items;
    }

    function updateSearchTerm(searchValue) {
        searchTerm = searchValue;
    }

    $: handleNewSearch(searchTerm);

</script>

<div class="flex justify-center relative">
    <input placeholder="Search a YouTube video" class="w-full px-6 py-4 text-lg bg-slate-700 rounded-md focus:outline-2 focus:outline-slate-400 focus:outline" bind:value={searchValue} on:change={() => updateSearchTerm(searchValue)} />
    <div class="absolute top-0 h-full right-3 flex items-center">
        <button class="px-4 py-2 bg-slate-900 text-gray-200 uppercase h-fit rounded">Search</button>
    </div>
</div>

<div class="w-full my-8">

    {#if videos}
        {#each videos as video}
        <div class="w-full h-28 my-6 bg-slate-600 rounded-xl overflow-hidden flex justify-between">
            <img src={video.snippet.thumbnails.high.url} alt="" class="aspect-video h-full object-cover">
            <section class="px-6 py-3 overflow-hidden flex-grow">
                <h3 class="text-xl font-semibold">{video.snippet.title}</h3>
                <!-- <p class="text-sm">{video.snippet.description}</p> -->
            </section>
            <section class="aspect-square h-full flex justify-center items-center border-l-2 border-l-solid border-l-slate-500">
                <button class="bg-green-700 w-1/2 aspect-square text-2xl rounded-2xl">D</button>
            </section>
        </div>
        {/each}
    {/if}

</div>