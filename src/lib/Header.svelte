<script>
  export let currentSection;
  export let setSection;
</script>

<header class="header-hero flex flex-col md:flex-row gap-4 md:gap-5 items-center justify-between">
  <div>
    <h1 class="hero-title text-2xl md:text-3xl">Hello. I'm <span style="text-decoration:underline">Inxeoz</span>.</h1>
    <p class="illustr-accent">a small portfolio with a retro twist</p>
  </div>
  <div class="mascot w-32 h-32 md:w-40 md:h-40">
    <!-- placeholder for mascot illustration -->
    <svg width="100" height="100" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
      <rect x="6" y="6" width="88" height="88" fill="#fff" stroke="#000" stroke-width="4" rx="10" />
      <circle cx="50" cy="45" r="14" fill="#000" />
      <rect x="30" y="68" width="40" height="8" fill="#000" />
    </svg>
  </div>
</header>

<nav class="mt-4 mb-6">
  <ul class="flex flex-row flex-wrap gap-2 md:gap-4">
    <li><button on:click={() => setSection('home')} class="text-sm {currentSection === 'home' ? 'underline' : ''}">Home</button></li>
    <li><button on:click={() => setSection('blog')} class="text-sm {currentSection === 'blog' ? 'underline' : ''}">Blog</button></li>
    <li><button on:click={() => setSection('about')} class="text-sm {currentSection === 'about' ? 'underline' : ''}">About</button></li>
    <li><button on:click={() => setSection('contact')} class="text-sm {currentSection === 'contact' ? 'underline' : ''}">Contact</button></li>
  </ul>
</nav>