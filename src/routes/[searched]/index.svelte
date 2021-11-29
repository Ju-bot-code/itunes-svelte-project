

<script>
    import {page} from '$app/stores';
    import {onMount} from 'svelte'; 
    import {goto} from '$app/navigation';

    let searchResults=[];

    let fetched =$page.params.searched ;
    onMount( async ()=>{
        const res = await fetch(`https://itunes.apple.com/search?term=${fetched}`);
        const data = await res.json();
        // console.log(data.results);
        searchResults=data.results;
      
    })
  

    
</script>
<h1 class="text-center text-3xl font-thin text-white mb-4 uppercase">{$page.params.searched}</h1>

<section>
    
    <div class="grid grid-cols-3 gap-4 text-white ">
        {#each searchResults as song}
            <button on:click="{ goto(`${fetched}/${song.trackId}`)}" class="p-4 border-2 text-white  font-thin bg-white bg-opacity-20 border-white rounded-md m-2 border-opacity-40" >
               <div class="flex  items-center justify-center space-x-3 py-2">
                   
                   <img src="{song.artworkUrl100}" class="w-1/4 rounded-md object-cover" alt="{song.trackName}">
                    <div class="flex  flex-col">
                        <p class="">{song.trackName}</p>
                        <p class="uppercase">{song.artistName}</p>
                    </div>
               </div> 
            </button>
        {:else}
            {#if searchResults.length > 0}
            <div class="col-span-3 ">
                <p class="flex text-opacity-70 justify-center space-x-3 items-center  text-white">Loading..</p>
            </div>
            {:else}
            <div class="col-span-3 ">
                <p class="flex text-opacity-70 justify-center space-x-3 items-center  text-white ">
                    <span> no results found..!</span>
                    <svg xmlns="http://www.w3.org/2000/svg" class="  h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                        <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM7 9a1 1 0 100-2 1 1 0 000 2zm7-1a1 1 0 11-2 0 1 1 0 012 0zm-7.536 5.879a1 1 0 001.415 0 3 3 0 014.242 0 1 1 0 001.415-1.415 5 5 0 00-7.072 0 1 1 0 000 1.415z" clip-rule="evenodd" />
                    </svg>
                </p>
            </div>
            {/if}
            
        {/each}
    </div>
    

   
</section>

