<script context="module">
    export async function load({page}){
        let trackid=page.params.tackid; 
        const res =await fetch(`https://itunes.apple.com/search?term=${trackid}&entity=song`);
        const data = await res.json();
        let song=data.results[0];
        return {props :{song}}
    }
</script>



<script>
    import {goto} from '$app/navigation';
  export let song;
  console.log(song);
    
</script>

<h1 class="text-2xl uppercase font-thin text-white text-center">{song.trackName}</h1>
<div class="flex flex-col items-center space-y-6 my-6">
    <img src="{song.artworkUrl100}"  class="w-1/6 object-cover"  alt="{song.trackName}">
    <audio controls>
        <source src={song.previewUrl} type="audio/mpeg">
    </audio>
    <button on:click="{goto(`/artist/${song.artistId}`)}">
<!-- https://itunes.apple.com/lookup?id=${song.artistid}` -->
        <h2 class=" font-thin text-white"> @{song.artistName}</h2>
    </button>
</div>