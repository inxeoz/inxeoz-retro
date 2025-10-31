<script>
  export let title;
  export let description;
  export let codeLink;
  export let siteLink;
  export let skills = [];
</script>

  <article class="card-projects">
  <h3 class="font-bold text-lg">{title}</h3>
  <p class="mt-2 text-sm">{description}</p>
  {#if skills.length > 0}
    <div class="mt-2 flex flex-wrap gap-1">
      {#each skills as skill}
        <span class="text-xs bg-gray-200 px-2 py-1 rounded">{skill}</span>
      {/each}
    </div>
  {/if}
  <div class="mt-4 flex gap-2">
    {#if siteLink}
      <a class="inline-block px-3 py-2 border-2 flex items-center gap-1" href={siteLink} target="_blank" rel="noopener">
        🌐 Website
      </a>
    {/if}
    {#if codeLink}
      <a class="inline-block px-3 py-2 border-2 flex items-center gap-1" href={codeLink} target="_blank" rel="noopener">
        🐱 GitHub
      </a>
    {/if}
  </div>
</article>