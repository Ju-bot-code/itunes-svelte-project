<script>
    import '../../src/tailwind.css'
    import  Header from '../routes/component/header.svelte'
</script>

<div class="bg-gradient-to-r min-h-screen from-purple-400 via-pink-500 to-red-500 ">
    <h1 class="text-2xl py-3 text-white uppercase text-center font-thin">find new music</h1>
    <div class="max-w-6xl space-y-4  mx-auto p-20 ">
        <Header/>
       
        <slot></slot>
    </div>
</div>

