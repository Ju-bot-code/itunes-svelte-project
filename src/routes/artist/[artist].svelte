<script context="module">
    export async function load({page})
    {
        const id=page.params.artist;
        const res =await fetch(`https://itunes.apple.com/lookup?id=${id}`);
        const data=await res.json();
        let artist=data.results[0];
        return {props:{artist}}
    }

</script>
<script>
    export let artist;
    // console.log(artist);
</script>
<div class="space-y-3 text-white flex flex-col justify-center items-center">

    <h1 class="text-3xl font-thin uppercase">{artist.artistName}</h1>
    <h2 class="text-xl font-thin">Primary gener : {artist.primaryGenreName}</h2>
    
    <!-- <a href="{artist.artistLinkUrl}" class="border border-white border-opacity-45 bg-white bg-opacity-30 py-2 px-3 rounded-md">visit</a> -->
</div>