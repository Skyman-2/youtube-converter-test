<script>
    import "../app.css";
</script>

<header class="flex justify-between bg-slate-950 px-60 py-6 m-0 text-gray-200">
    <div>
        <h2 class="text-2xl uppercase">Convertomatron</h2>
    </div>

    <nav class="flex align-middle gap-4">
        <a href="/" class="text-lg">Home</a>
        <a href="/about" class="text-lg">About</a>
    </nav>
</header>

<main class="text-gray-200 mx-60 my-24 p-0">
    <slot />
</main>