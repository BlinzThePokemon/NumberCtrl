<script>
    import '../app.css';
    import { page } from '$app/state';
    let { children } = $props();
    let navBarItems = [
        { name: 'Website Countdown', id: '/' },
        { name: 'Page Countdown', id: '/Pageccountdown' },
        { name: 'Contact Us', id: '/Contact' },
        { name: 'About', id: '/About' }
    ];
</script>

<nav class="shadow-md backdrop-blur-xl fixed w-screen top-0 z-20">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <div class="flex h-16 items-center justify-center">
            <div class="hidden space-x-4 sm:flex">
                {#each navBarItems as item}
                    {@const path = page.url.pathname.split('/')[1]}
                    {@const selected = path === item.id.split('/')[1]}

                    <a
                        class:bg-gray-900={selected}
                        class:text-white={selected}
                        href={item.id}
                        class="rounded-md px-3 py-2 text-sm font-medium transition duration-300 ease-in-out hover:bg-gray-500 hover:text-white active:bg-gray-900 active:text-white"
                        >{item.name}
                    </a>
                {/each}
            </div>
        </div>
    </div>
</nav>

{@render children()}