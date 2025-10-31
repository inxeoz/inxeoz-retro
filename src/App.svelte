<script>
  import Header from './lib/Header.svelte';
  import ProjectCard from './lib/ProjectCard.svelte';
  import BlogCard from './lib/BlogCard.svelte';
  import CodeBlock from './lib/CodeBlock.svelte';
  import Footer from './lib/Footer.svelte';

  let currentSection = 'home';
  let selectedPost = null;
  let activeFavTab = 'YOUTBERS';

  const projects = [
    {
      title: 'CHAK A VERSION CONTROL SYSTEM',
      description: 'I tried to build a version control system in Rust inspired by Git. Although it\'s not complete, it is easily understandable and extendable',
      codeLink: 'https://github.com/inxeoz/chak',
      skills: ['svelte', 'penpot', 'nodejs', 'rust']
    },
    {
      title: 'MUSIC ARTIST VARN\'S PORTFOLIO',
      description: 'It\'s kind of a personal project. In this project, I built a portfolio for my friend Varn. He is a music artist and dancer, currently in the early stage of his career. So, this project is a kind of gift to him',
      siteLink: 'https://varn.inxeoz.com/',
      codeLink: 'https://github.com/inxeoz/varn_proj',
      skills: ['svelte', 'penpot', 'nodejs', 'aws']
    },
    {
      title: 'BRAINFLEX MATHEMATICAL EQ. BASED GAME',
      description: 'As a fun project, I started Brainflex. At that time, I had no experience with game development, so I began learning the Godot engine and started building games. Brainflex is a result of that learning process',
      codeLink: 'https://github.com/inxeoz/brainFlex',
      skills: ['godot engine', 'godot script', 'android development', 'game development']
    },
    {
      title: 'Phonetic converter using RUST -> WASM -> JS',
      description: 'I wanted to improve my English pronunciation, so I needed a site that converts English words to IPA. Although there are many sites available with this functionality, I wanted to implement my own. The frontend part is not complete yet, but the Penpot design has been finished.',
      codeLink: 'https://github.com/inxeoz/svelte_phonetic',
      skills: ['svelte', 'WASM', 'RUST', 'nodejs']
    }
  ];

  const blogPosts = [
    {title: 'Welcome to my blog', excerpt: 'Small notes and experiments with retro UI.', date: '2023-11-01', content: [{type: 'text', value: 'This is the full content of the welcome post. Here I talk about starting this blog and my experiments with retro UI designs. It\'s all about creating tactile, monochrome layouts that feel good to interact with.'}]},
    {title: 'Designing with monochrome', excerpt: 'How black and white can create tactile layouts.', date: '2023-10-15', content: [{type: 'text', value: 'Monochrome design isn\'t just about aesthetics—it\'s about focus and usability. By removing color distractions, we can create interfaces that emphasize form, texture, and interaction. This post explores techniques for making black and white designs engaging.'}]},
    {title: 'Svelte for portfolios', excerpt: 'Why I chose Svelte for this project.', date: '2023-09-20', content: [{type: 'text', value: 'Svelte offers a unique approach to building web apps with its compile-time optimization. For a portfolio site, this means fast loading times and smooth interactions. I chose Svelte because it allows me to write less code while achieving more performance.'}]},
    {title: 'Setting up a Svelte project', excerpt: 'Quick guide to getting started with Svelte.', date: '2023-10-05', content: [
      {type: 'text', value: 'To create a new Svelte project, run the following commands:'},
      {type: 'code', value: 'npx create-svelte@latest my-app\ncd my-app\nnpm install\nnpm run dev', lang: 'bash'},
      {type: 'text', value: 'This will set up a basic Svelte app with Vite. For more options, check the Svelte docs.'}
    ]}
  ];

  const favContent = {
    YOUTBERS: [
      {text: 'PHYSICS VIDEOS BY EUGENE KHUTORYANSKY', url: 'https://www.youtube.com/@EugeneKhutoryansky'},
      {text: 'ALAN BECKER', url: 'https://www.youtube.com/@alanbecker'},
      {text: 'BRANCH EDUCATION', url: 'https://www.youtube.com/@BranchEducation'},
      {text: 'KHAN ACADEMY', url: 'https://www.youtube.com/@khanacademy'},
      {text: '3B1B', url: 'https://www.youtube.com/@3blue1brown'},
      {text: 'VERITASIUM', url: 'https://www.youtube.com/@veritasium'},
      {text: 'LESICS', url: 'https://www.youtube.com/@SabinCivil'},
      {text: 'SARTHAK GOSWAMI', url: 'https://www.youtube.com/@SundaySarthak'}
    ],
    'SITE:S': [
      {text: 'mathsisfun.com', url: 'https://www.mathsisfun.com/'},
      {text: 'egyankosh.ac.in', url: 'https://egyankosh.ac.in/handle/123456789/17990?mode=full'},
      {text: 'zerotomastery.io', url: 'https://zerotomastery.io/'},
      {text: 'osdev.org', url: 'https://wiki.osdev.org/Expanded_Main_Page'},
      {text: 'dogl.app', url: 'https://www.dogl.app/'}
    ],
    QUOTES: [
      ' "EACH AND EVERY TYPE OF PROBLEM HAS ALWAYS A SOLUTION" ',
      ' "YOU CAN\'T BE ONLINE EVERY TIME , BE READY FOR OFFLINE MODE" ',
      ' "KEEP BREATHING , TIDE WILL COME TAKE SOMEWHERE ; DON\'T GIVE UP" '
    ].map(q => ({text: q, url: `https://www.google.com/search?q=${encodeURIComponent(q)}`})),
    BOOKS: ['Gunaho Ka Devta', 'The Mastery Of Love [READING]'].map(q => ({text: q, url: `https://www.google.com/search?q=book: ${encodeURIComponent(q)}`}))
  };

  const favTabs = Object.keys(favContent);

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
          <ProjectCard title={p.title} description={p.description} codeLink={p.codeLink} siteLink={p.siteLink} skills={p.skills} />
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
        <div class="card-blogs p-6">
          <h3 class="text-xl font-bold mb-2">{selectedPost.title}</h3>
          <p class="text-sm text-gray-600 mb-4">{selectedPost.date}</p>
          <div class="text-base leading-relaxed">
            {#each selectedPost.content as block}
              {#if block.type === 'text'}
                <p class="mb-4">{block.value}</p>
              {:else if block.type === 'code'}
                <CodeBlock code={block.value} lang={block.lang} />
              {/if}
            {/each}
          </div>
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
      <img src="https://avatars.githubusercontent.com/inxeoz" alt="avatar" class="w-24 h-24 md:w-28 md:h-28 border-2 border-black rounded-none mx-auto md:mx-0" style="border-width: 3px;" />
      <div>
        <p>I am Purushottam, software developer, designer, research enthusiast...</p>
        <p>Even I don't know myself—what the hell am I?</p>
      </div>
      </div>
    </section>
  {/if}

  {#if currentSection === 'contact'}
    <section class="mt-6">
      <h2 class="text-2xl font-bold">Contact</h2>
      <div class="mt-4 card-blogs p-4">
        <p>Email: <a href="mailto:hello@inxeoz.com">hello@inxeoz.com</a></p>
        <p class="mt-2">Social: <a href="https://github.com/inxeoz/">GitHub</a> · <a href="https://dribbble.com/inxeoz">Dribbble</a> · <a href="https://www.linkedin.com/in/purushottam-singram/">LinkedIn</a> · <a href="https://medium.com/@inxeoz">Medium</a></p>
      </div>
    </section>
  {/if}

  {#if currentSection === 'favorites'}
    <section class="mt-6">
      <h2 class="text-2xl font-bold">Favorites</h2>
      <div class="mt-4">
        <div class="flex flex-wrap gap-2 mb-4">
          {#each favTabs as tab}
            <button
              class="px-3 py-2 border-2 {activeFavTab === tab ? 'bg-black text-white' : ''}"
              on:click={() => activeFavTab = tab}
            >
              {tab}
            </button>
          {/each}
        </div>
        <div class="card-bw p-4">
          <div class="flex flex-col gap-2">
            {#each favContent[activeFavTab] as item}
              <a href={item.url} target="_blank" rel="noopener" class="text-blue-600 underline hover:text-blue-800">
                {item.text}
              </a>
            {/each}
          </div>
        </div>
      </div>
    </section>
  {/if}

  <Footer />
</div>

<style>
  @import './app.css';
</style>