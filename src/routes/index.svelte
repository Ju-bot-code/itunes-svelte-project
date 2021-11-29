<script>
    import {goto} from '$app/navigation';
    let searched='';
    const searching =()=>{
        goto(`${searched}`);
    }

</script>



<label for="search" class="text-3xl block text-white font-thin text-center">Search Artist</label>
<section class="text-white font-thin flex space-x-4 justify-center">
    <div class="  border rounded-md bg-white bg-opacity-30 p-1 space-x-6">
        <input placeholder="FIND SONGS" class="bg-transparent  focus:border-none rounded-md focus:bg-transparent focus:outline-none placeholder-white placeholder-opacity-25 p-1 px-4" type="text" id="search" name="search" bind:value={searched}>
        <button on:click="{searching}" class="relative p-1 border bg-white rounded-md text-gray-700 font-thin">seach it!</button>
    </div>
</section>
