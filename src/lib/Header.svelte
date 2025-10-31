<script>
  export let currentSection;
  export let setSection;
</script>

<header class="header-hero flex flex-col md:flex-row gap-4 md:gap-5 items-center justify-between">
  <div>
    <h1 class="hero-title text-2xl md:text-3xl">Hello. I'm <span style="text-decoration:underline">Purushottam</span>.</h1>
    <p class="illustr-accent">a small portfolio with a retro twist</p>
  </div>
  <div class="mascot w-32 h-32 md:w-40 md:h-40">
    <img src="https://avatars.githubusercontent.com/inxeoz" alt="mascot" class="w-full h-full object-cover rounded-xl" />
  </div>
</header>

<nav class="mt-4 mb-6">
  <ul class="flex flex-row flex-wrap gap-2 md:gap-4">
    <li><button on:click={() => setSection('home')} class="text-sm {currentSection === 'home' ? 'underline' : ''}">Home</button></li>
    <li><button on:click={() => setSection('blog')} class="text-sm {currentSection === 'blog' ? 'underline' : ''}">Blog</button></li>
    <li><button on:click={() => setSection('about')} class="text-sm {currentSection === 'about' ? 'underline' : ''}">About</button></li>
    <li><button on:click={() => setSection('favorites')} class="text-sm {currentSection === 'favorites' ? 'underline' : ''}">Favorites</button></li>
    <li><button on:click={() => setSection('contact')} class="text-sm {currentSection === 'contact' ? 'underline' : ''}">Contact</button></li>
  </ul>
</nav>