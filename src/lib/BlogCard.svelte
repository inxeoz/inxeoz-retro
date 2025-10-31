<script>
  export let title;
  export let excerpt;
  export let date;
  export let onClick;
</script>

<article class="card-bw cursor-pointer" on:click={onClick}>
  <h3 class="font-bold text-lg">{title}</h3>
  <p class="mt-2 text-sm">{excerpt}</p>
  <p class="mt-2 text-xs text-gray-600">{date}</p>
  <div class="mt-4">
    <button class="inline-block px-3 py-2 border-2">Read more</button>
  </div>
</article>