<script>
  export let title;
  export let excerpt;
  export let date;
  export let link = '#';
</script>

<article class="card-bw">
  <h3 class="font-bold text-lg">{title}</h3>
  <p class="mt-2 text-sm">{excerpt}</p>
  <p class="mt-2 text-xs text-gray-600">{date}</p>
  <div class="mt-4">
    <a class="inline-block px-3 py-2 border-2" href={link}>Read more</a>
  </div>
</article>