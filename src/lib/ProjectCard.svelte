<script>
  export let title;
  export let description;
  export let link = '#';
  export let skills = [];
</script>

<article class="card-bw">
  <h3 class="font-bold text-lg">{title}</h3>
  <p class="mt-2 text-sm">{description}</p>
  {#if skills.length > 0}
    <div class="mt-2 flex flex-wrap gap-1">
      {#each skills as skill}
        <span class="text-xs bg-gray-200 px-2 py-1 rounded">{skill}</span>
      {/each}
    </div>
  {/if}
  <div class="mt-4">
    <a class="inline-block px-3 py-2 border-2" href={link} target="_blank" rel="noopener">View project</a>
  </div>
</article>