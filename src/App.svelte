<script>
  import Header from './lib/Header.svelte';
  import ProjectCard from './lib/ProjectCard.svelte';
  import BlogCard from './lib/BlogCard.svelte';
  import Footer from './lib/Footer.svelte';

  let currentSection = 'home';
  let selectedPost = null;

  const projects = [
    {title: 'Possimus', description: 'Retro layout experiment.', image: '/images/proj1.jpg'},
    {title: 'Dolorum', description: 'Black & white photo series', image: '/images/proj2.jpg'}
  ];

  const blogPosts = [
    {title: 'Welcome to my blog', excerpt: 'Small notes and experiments with retro UI.', date: '2023-11-01', content: 'This is the full content of the welcome post. Here I talk about starting this blog and my experiments with retro UI designs. It\'s all about creating tactile, monochrome layouts that feel good to interact with.'},
    {title: 'Designing with monochrome', excerpt: 'How black and white can create tactile layouts.', date: '2023-10-15', content: 'Monochrome design isn\'t just about aesthetics—it\'s about focus and usability. By removing color distractions, we can create interfaces that emphasize form, texture, and interaction. This post explores techniques for making black and white designs engaging.'},
    {title: 'Svelte for portfolios', excerpt: 'Why I chose Svelte for this project.', date: '2023-09-20', content: 'Svelte offers a unique approach to building web apps with its compile-time optimization. For a portfolio site, this means fast loading times and smooth interactions. I chose Svelte because it allows me to write less code while achieving more performance.'}
  ];

  function setSection(section) {
    currentSection = section;
    selectedPost = null; // Reset when switching sections
  }

  function selectPost(post) {
    selectedPost = post;
  }

  function backToBlog() {
    selectedPost = null;
  }
</script>

<div class="container-retro">
  <Header {currentSection} {setSection} />

  {#if currentSection === 'home'}
    <section class="mt-6">
      <h2 class="text-2xl font-bold">Projects</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4 md:gap-6 mt-4">
        {#each projects as p}
          <ProjectCard title={p.title} description={p.description} image={p.image} />
        {/each}
      </div>
    </section>
  {/if}

  {#if currentSection === 'blog'}
    <section class="mt-6">
      {#if selectedPost}
        <div class="flex items-center justify-between mb-4">
          <h2 class="text-2xl font-bold">Blog</h2>
          <button on:click={backToBlog} class="text-sm underline">← Back to Blog</button>
        </div>
        <div class="card-bw p-6">
          <h3 class="text-xl font-bold mb-2">{selectedPost.title}</h3>
          <p class="text-sm text-gray-600 mb-4">{selectedPost.date}</p>
          <p class="text-base leading-relaxed">{selectedPost.content}</p>
        </div>
      {:else}
        <h2 class="text-2xl font-bold">Blog</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 md:gap-6 mt-4">
          {#each blogPosts as post}
            <BlogCard title={post.title} excerpt={post.excerpt} date={post.date} onClick={() => selectPost(post)} />
          {/each}
        </div>
      {/if}
    </section>
  {/if}

  {#if currentSection === 'about'}
    <section class="mt-6">
      <h2 class="text-2xl font-bold">About</h2>
      <div class="mt-4 card-bw p-4 flex flex-col md:flex-row gap-4">
        <div class="w-24 h-24 md:w-28 md:h-28 border-2 border-black rounded-xl flex items-center justify-center mx-auto md:mx-0" style="border-width: 3px;">avatar</div>
        <div>
          <p>Hi — I'm Inxeoz, a maker who likes retro UI, tactile layouts and small interactive experiments. I combine monochrome structure with friendly illustrated accents.</p>
        </div>
      </div>
    </section>
  {/if}

  {#if currentSection === 'contact'}
    <section class="mt-6">
      <h2 class="text-2xl font-bold">Contact</h2>
      <div class="mt-4 card-bw p-4">
        <p>Email: <a href="mailto:hello@inxeoz.com">hello@inxeoz.com</a></p>
        <p class="mt-2">Social: <a href="#">Twitter</a> · <a href="#">GitHub</a></p>
      </div>
    </section>
  {/if}

  <Footer />
</div>

<style>
  @import './app.css';
</style>